# 变量

自定义变量 , 更好的设计 .

Bulma有两个变量文件 , 分为4部分 :

**1.初始变量\(Initial variables\)** : 通过literal value文本值定义变量的位置 , 如 :

* **colors **: $blue: hsl\(217, 71%, 53%\)
* **font sizes **: $size-1: 3rem
* **dimensions **: $gap: 32px
* **other values **: $easing: ease-out or $radius-large: 5px

**2.派生变量\(Derived variables\)** : 从上一文件中设置的值计算变量的派生变量

从初始变量派生的主要颜色 :

* $primary: $turquoise
* $link: $blue
* $info: $cyan
* $success: $green
* $warning: $yellow
* $danger: $red
* $dark: $grey-darker
* $text: $grey-dark

`$background: $white-ter` : 一般背景色  
`$link: $blue` : 链接使用的主要颜色  
`$family-primary: $family-sans-serif` : 主要字体系列是sans-serif

"列表和映射"是集合 , 所以是已经定义的变量 :

* `$colors: ("white": ($white, $black), "black": ($black, $white), "light": ($light, $light-invert), "dark": ($dark, $dark-invert), "primary": ($primary, $primary-invert), "link": ($link, $link-invert), "info": ($info, $info-invert), "success": ($success, $success-invert), "warning": ($warning, $warning-invert), "danger": ($danger, $danger-invert))`
* `$shades: ("black-bis": $black-bis, "black-ter": $black-ter, "grey-darker": $grey-darker, "grey-dark": $grey-dark, "grey": $grey, "grey-light": $grey-light, "grey-lighter": $grey-lighter, "white-ter": $white-ter, "white-bis": $white-bis)`
* `$sizes: $size-1 $size-2 $size-3 $size-4 $size-5 $size-6 $size-7`

**要覆盖这些变量中的任何一个 , 只需在导入Bulma之前设置它们即可 . **

---

#### **初始变量**

这些变量是具有文本值的 .

| `$black` | `hsl(0, 0%, 4%)` |
| :--- | :--- |
| `$black-bis` | `hsl(0, 0%, 7%)` |
| `$black-ter` | `hsl(0, 0%, 14%)` |
| `$grey-darker` | `hsl(0, 0%, 21%)` |
| `$grey-dark` | `hsl(0, 0%, 29%)` |
| `$grey` | `hsl(0, 0%, 48%)` |
| `$grey-light` | `hsl(0, 0%, 71%)` |
| `$grey-lighter` | `hsl(0, 0%, 86%)` |
| `$white-ter` | `hsl(0, 0%, 96%)` |
| `$white-bis` | `hsl(0, 0%, 98%)` |
| `$white` | `hsl(0, 0%, 100%)` |
| `$orange` | `hsl(14, 100%, 53%)` |
| `$yellow` | `hsl(48, 100%, 67%)` |
| `$green` | `hsl(141, 71%, 48%)` |
| `$turquoise` | `hsl(171, 100%, 41%)` |
| `$cyan` | `hsl(204, 86%, 53%)` |
| `$blue` | `hsl(217, 71%, 53%)` |
| `$purple` | `hsl(271, 100%, 71%)` |
| `$red` | `hsl(348, 100%, 61%)` |
| `$family-sans-serif` | `BlinkMacSystemFont, -apple-system, "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue", "Helvetica", "Arial", sans-serif` |
| `$family-monospace` | `monospace` |
| `$render-mode` | `optimizeLegibility` |
| `$size-1` | `3rem` |
| `$size-2` | `2.5rem` |
| `$size-3` | `2rem` |
| `$size-4` | `1.5rem` |
| `$size-5` | `1.25rem` |
| `$size-6` | `1rem` |
| `$size-7` | `0.75rem` |
| `$weight-light` | `300` |
| `$weight-normal` | `400` |
| `$weight-medium` | `500` |
| `$weight-semibold` | `600` |
| `$weight-bold` | `700` |
| `$gap` | `32px` |
| `$tablet` | `769px` |
| `$desktop` | `960px + (2 * $gap)` |
| `$widescreen` | `1152px + (2 * $gap)` |
| `$fullhd` | `1344px + (2 * $gap)` |
| `$easing` | `ease-out` |
| `$radius-small` | `2px` |
| `$radius` | `3px` |
| `$radius-large` | `5px` |
| `$speed` | `86ms` |

---

#### 派生变量

这些变量具有引用另一个变量的值 .

| `$primary` | `$turquoise` |
| :--- | :--- |
| `$info` | `$cyan` |
| `$success` | `$green` |
| `$warning` | `$yellow` |
| `$danger` | `$red` |
| `$light` | `$white-ter` |
| `$dark` | `$grey-darker` |
| `$orange-invert` | `findColorInvert($orange)` |
| `$yellow-invert` | `findColorInvert($yellow)` |
| `$green-invert` | `findColorInvert($green)` |
| `$turquoise-invert` | `findColorInvert($turquoise)` |
| `$cyan-invert` | `findColorInvert($cyan)` |
| `$blue-invert` | `findColorInvert($blue)` |
| `$purple-invert` | `findColorInvert($purple)` |
| `$red-invert` | `findColorInvert($red)` |
| `$primary-invert` | `$turquoise-invert` |
| `$info-invert` | `$cyan-invert` |
| `$success-invert` | `$green-invert` |
| `$warning-invert` | `$yellow-invert` |
| `$danger-invert` | `$red-invert` |
| `$light-invert` | `$dark` |
| `$dark-invert` | `$light` |
| `$background` | `$white-ter` |
| `$border` | `$grey-lighter` |
| `$border-hover` | `$grey-light` |
| `$text` | `$grey-dark` |
| `$text-invert` | `findColorInvert($text)` |
| `$text-light` | `$grey` |
| `$text-strong` | `$grey-darker` |
| `$code` | `$red` |
| `$code-background` | `$background` |
| `$pre` | `$text` |
| `$pre-background` | `$background` |
| `$link` | `$blue` |
| `$link-invert` | `$blue-invert` |
| `$link-visited` | `$purple` |
| `$link-hover` | `$grey-darker` |
| `$link-hover-border` | `$grey-light` |
| `$link-focus` | `$grey-darker` |
| `$link-focus-border` | `$blue` |
| `$link-active` | `$grey-darker` |
| `$link-active-border` | `$grey-dark` |
| `$family-primary` | `$family-sans-serif` |
| `$family-code` | `$family-monospace` |
| `$size-small` | `$size-7` |
| `$size-normal` | `$size-6` |
| `$size-medium` | `$size-5` |
| `$size-large` | `$size-4` |
| `$colors` | `("white": ($white, $black), "black": ($black, $white), "light": ($light, $light-invert), "dark": ($dark, $dark-invert), "primary": ($primary, $primary-invert), "link": ($link, $link-invert), "info": ($info, $info-invert), "success": ($success, $success-invert), "warning": ($warning, $warning-invert), "danger": ($danger, $danger-invert))` |
| `$shades` | `("black-bis": $black-bis, "black-ter": $black-ter, "grey-darker": $grey-darker, "grey-dark": $grey-dark, "grey": $grey, "grey-light": $grey-light, "grey-lighter": $grey-lighter, "white-ter": $white-ter, "white-bis": $white-bis)` |
| `$sizes` | `$size-1 $size-2 $size-3 $size-4 $size-5 $size-6 $size-7` |

---

#### 泛型变量

可以使用以下通用变量进行常规自定义 . 在导入Bulma之前 , 只需设置一个或多个这些变量 .

| `$body-background-color` | `#fff` |
| :--- | :--- |
| `$body-size` | `16px` |
| `$body-rendering` | `optimizeLegibility` |
| `$body-family` | `$family-primary` |
| `$body-color` | `$text` |
| `$body-weight` | `$weight-normal` |
| `$body-line-height` | `1.5` |
| `$code-family` | `$family-code` |
| `$code-padding` | `0.25em 0.5em 0.25em` |
| `$code-weight` | `normal` |
| `$code-size` | `0.875em` |
| `$hr-background-color` | `$border` |
| `$hr-height` | `1px` |
| `$hr-margin` | `1.5rem 0` |
| `$strong-color` | `$text-strong` |
| `$strong-weight` | `$weight-bold` |



