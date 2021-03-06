# Draft of the JavaScript API

This is currently a work in progress, expect the API to change significantly.
Specifically, the APIs returning strings as results of inspection should return
structured data instead for ease of use.

```js
class LLNode {
  /**
   * @param {string} dump path to the coredump
   * @param {string} executable path to the node executable
   * @returns {LLNode} an LLNode instance
   */
  static fromCoredump(dump, executable) {}

  /**
   * @returns {string} SBProcess information
   */
  getProcessInfo() {}

  /**
   * @typedef {object} Frame
   * @property {string} function
   *
   * @typedef {object} Thread
   * @property {number} threadId
   * @property {number} frameCount
   * @property {Frame[]} frames
   *
   * @typedef {object} Process
   * @property {number} pid
   * @property {string} state
   * @property {number} threadCount
   * @property {Thread[]} threads
   *
   * @returns {Process} Process data
   */
  getProcessObject() {}

  /**
   * @typedef {object} HeapInstance
   * @property {string} address
   * @property {string} value
   *
   * @typedef {object} HeapType
   * @property {string} typeName
   * @property {string} instanceCount
   * @property {string} totalSize
   * @property {LLNode} llnode
   * @property {Iterator<HeapInstance>} instances
   *
   * @returns {HeapType[]}
   */
  getHeapTypes() {}

  /**
   * TODO: rematerialize object
   * @returns {HeapInstance}
   */
  getObjectAtAddress(address) {}
}
```
