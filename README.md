```javascript
<script>
export default {
  data() {
    return {
      message: '変更前'
    }
  },
  beforeCreate: function() {
    // インスタンス作成・dataオブジェクトへのアクセス不可能
    console.log('beforeCreate')
    // undefinded
    console.log(this.message)

    // インスタンスは作成されているので、値をセットした後にconsole.logすれば表示は可能(保存はされない)一時的にセットしてるだけ
    this.message = '値をセットしたよ！'
    console.log(this.message)
  },
  created: function() {
    // インスタンス作成・dataオブジェクトのアクセス可能
    console.log('created')
    // 変更前
    console.log(this.message)
  },
  beforeMount: function() {
    // DOM未作成・DOMへのアクセス不可(undefinded)
    console.log('beforeMount')
    // undefindedが返る
    console.log(this.$el)
  },
  mounted: function() {
    // DOM作成(マウントされた後)・DOMへのアクセス可能(<div id="app">...</div>)
    // SSRの場合は使えない
    console.log('mounted')
    // 要素が返る
    console.log(this.$el)
  },
  // データの更新時にはrenderされるので、この前後でフックが可能
  beforeUpdate: function() {
    // 更新前の既存のDOMにたいしてアクセスできる
    console.log('beforeUpdate')
    // SSRの場合使えない
  },
  updated: function() {
    // データの更新が合った時、render後に実行される
    // SSRの場合使えない
  },
  // インスタンスの削除 $destroy()が呼ばれた時にこの前後でフックが可能
  beforeDestroy: function() {
    // $destroy()が呼ばれた後、インスタンスが削除される前に実行される
    // SSRの場合使えない
  },
  destroyed: function(){
    // $destroy()が呼ばれた後、インスタンスが削除された後に実行される
    // SSRの場合は使えない
  }
}
```
