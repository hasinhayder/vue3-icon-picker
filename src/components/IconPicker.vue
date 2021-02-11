<template>
  <span v-bind="$attrs" @click="togglePicker">
    <i class="vue3-icon-picker" :class="modelValue"></i>
  </span>

  <div class="aim-modal aim-open" v-if="isVisible">
    <div class="aim-modal--content">
      <div class="aim-modal--header">
        <div class="aim-modal--header-logo-area">
          <span class="aim-modal--header-logo-title">
            {{ label }}
          </span>
        </div>
        <div class="aim-modal--header-close-btn" @click="closePicker">
          <i class="fas fa-times" title="Close"></i>
        </div>
      </div>
      <div class="aim-modal--body">
        <div class="aim-modal--sidebar">
          <div class="aim-modal--sidebar-tabs">
            <div
              class="aim-modal--sidebar-tab-item"
              data-library-id="all"
              v-for="tab in tabs"
              :key="tab.id"
              :class="{ 'aesthetic-active': isActiveTab(tab.id) }"
              @click="setActiveTab(tab)"
            >
              <i :class="tab.icon"></i>
              <span>{{ tab.title }}</span>
            </div>
          </div>
          <div class="aim-sidebar-preview">
            <div class="aim-icon-item ">
              <div class="aim-icon-item-inner">
                <i :class="activeGlyph"></i>
                <div class="aim-icon-item-name">
                  {{ activeGlyph }}
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="aim-modal--icon-preview-wrap">
          <div class="aim-modal--icon-search">
            <input v-model="filterText" placeholder="Filter by name..." />
            <i class="fas fa-search"> </i>
          </div>
          <div class="aim-modal--icon-preview-inner">
            <div class="aim-modal--icon-preview">
              <div
                class="aim-icon-item"
                v-for="glyph in glyphs"
                :key="glyph"
                :class="{ 'aesthetic-selected': isActiveGlyph(glyph) }"
                @click="setActiveGlyph(glyph)"
              >
                <div class="aim-icon-item-inner">
                  <i :class="glyph"></i>
                  <div class="aim-icon-item-name">
                    {{ getGlyphName(glyph) }}
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="aim-modal--footer">
        <button class="aim-insert-icon-button" @click="insert">Insert</button>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, computed } from 'vue'
import fontLibrary from './data/fonts'

export default {
  inheritAttrs:false,
  props: {
    label: {
      type: String,
      default: 'Vue3 Icon Picker'
    },
    modelValue: {
      type: String,
      default: 'fas fa-circle'
    }
  },
  setup (props, context) {
    const filterText = ref('')
    const activeGlyph = ref(props.modelValue)
    const isVisible = ref(false)

    const tabs = [
      {
        id: 'all',
        title: 'All Icons',
        icon: 'fas fa-star-of-life',
        link: 'all'
      },
      {
        id: 'far',
        title: 'Font Awesome Regular',
        icon: 'fab fa-font-awesome-alt',
        link: fontLibrary.fontAwesome.variants.regular
      },
      {
        id: 'fas',
        title: 'Font Awesome Solid',
        icon: 'fab fa-font-awesome',
        link: fontLibrary.fontAwesome.variants.solid
      },
      {
        id: 'fab',
        title: 'Font Awesome Brands',
        icon: 'fab fa-font-awesome-flag',
        link: fontLibrary.fontAwesome.variants.brands
      }
    ]

    const activeTab = ref(tabs[0])

    const allGlyphs = [].concat(
      tabs[1].link.icons,
      tabs[2].link.icons,
      tabs[3].link.icons
    )

    const glyphs = computed(() => {
      let _glyphs = []
      if (activeTab.value.id !== 'all') {
        _glyphs = activeTab.value.link.icons
      } else {
        _glyphs = allGlyphs
      }

      if (filterText.value != '') {
        const _filterText = filterText.value.toLowerCase()
        _glyphs = _glyphs.filter(
          item => item.substr(7, filterText.value.length) === _filterText
        )
      }
      return _glyphs
    })

    const setActiveGlyph = glyph => {
      activeGlyph.value = glyph
    }

    const isActiveGlyph = glyph => {
      return activeGlyph.value == glyph
    }

    const isActiveTab = tab => {
      return tab == activeTab.value.id
    }

    const setActiveTab = tab => {
      activeTab.value = tab
      // filterText.value=''; //nice feature
    }

    const getGlyphName = glyph =>
      glyph.replace(/f.. fa-/g, '').replace('-', ' ')

    const insert = () => {
      context.emit('update:modelValue', activeGlyph.value)
      isVisible.value = false
    }

    const togglePicker = () => {
      isVisible.value = !isVisible.value
    }

    const closePicker = () => {
      isVisible.value = false
    }

    return {
      fontLibrary,
      tabs,
      isActiveTab,
      setActiveTab,
      glyphs,
      activeGlyph,
      getGlyphName,
      filterText,
      setActiveGlyph,
      isActiveGlyph,
      insert,
      isVisible,
      togglePicker,
      closePicker
    }
  }
}
</script>

<style scoped>
@import '../assets/css/style.css';
</style>
