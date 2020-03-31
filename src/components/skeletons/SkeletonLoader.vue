<script>
import SkeletonCard from './SkeletonCard';
import SkeletonTitle from './SkeletonTitle';
import SkeletonButton from './SkeletonButton';
import SkeletonText from './SkeletonText';
import SkeletonCardAction from './SkeletonCardAction';
export default {
  name: 'SkeletonLoader',
  functional: true,
  components: { SkeletonText, SkeletonButton, SkeletonTitle, SkeletonCard },
  props: {
    type: {
      type: String,
      default: 'card'
    },
    loading: {
      type: Boolean,
      default: true
    }
  },
  render(createElement, { props, slots, data }) {
    function getSkeletonType() {
      switch (props.type) {
        case 'card':
          return SkeletonCard;
        case 'card-action':
          return SkeletonCardAction;
        case 'title':
          return SkeletonTitle;
        case 'button':
          return SkeletonButton;
        case 'text':
          return SkeletonText;
        default:
          return SkeletonCard;
      }
    }
    const skeletonElement = createElement(getSkeletonType());
    const content = createElement(
      'div',
      {
        style: {
          display: props.loading ? 'none' : ''
        }
      },
      slots().default
    );
    const elements = props.loading ? [skeletonElement, content] : [content];
    return createElement('div', data, elements);
  }
};
</script>
