## Hard value (Base value will set manual)

- **Device:** Detect device
  ```js
  export enum Device {
  MOBILE = 'MOBILE',
  TABLET = 'TABLET',
  DESKTOP = 'DESKTOP'
  }
  export const CHECKPOINT_DEVICE: Record<number, Device> = {
  768: Device.TABLET,
  1024: Device.DESKTOP
  }
  ```
- **Column:** Total column layout depend on screen (section center)
  ```js
  export const CHECKPOINT_COLUMN: Record<number, number> = {
  768: 4,
  1024: 6
  }
  ```
- **Status Bar:** The header of layout (section top)
  ```js
  export const CHECKPOINT_HEIGHT_STATUS_BAR: Record<number, number> = {
  768: 60,
  1024: 40
  }`
  ```
- **Column dock:** Total column footer depend on screen (section bottom)
  ```js
  export const CHECKPOINT_COLUMN_DOCK: Record<number, number> = {
  768: 6,
  1024: 8
  }
  ```
- **Screen:** Max with of container (wrap all app in section center)
  ```js
  export const CHECKPOINT_SCREEN: Record<number, number> = {
  768: 768,
  1024: 1024
  }
  ```

## Calculate value (value depend on hard value)

- **Padding:**: Flow calculate: padding -> itemWidth

  - factor: hard data to calculate padding

```js
    const calculateGridDimensions = (screenWidth: number, columns: number) => {
    const factor = 20 // Adjusted based on user experience
    const outerPadding = screenWidth / (columns * factor)
    const gridGap = outerPadding // Gap between grid items
    const totalPadding = outerPadding * 2 + gridGap * (columns - 1)
    const itemWidth = (screenWidth - totalPadding) / columns
    return {
    itemWidth,
    outerPadding: totalPadding / 2 // Padding per side
    }
```
