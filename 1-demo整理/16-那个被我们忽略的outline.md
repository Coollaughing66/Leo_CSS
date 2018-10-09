> ԭ�����ߣ�^_^����John
> ԭ�ĵ�ַ��https://www.cnblogs.com/fsjohnhuang/p/9753554.html 

���ķ���һ�����������Ե����ԡ���outline������֮ǰ����ӡ��ȷʵ��Щģ�������Ǳ��Ĵ�����������΢������о�^_^

## Spec��������������
### ����
���ڴ������Ӷ��������(Ԫ�ص�`border-box`)�������ť�����ȡ�

### ��border��ͬ
* outline��ռ�ĵ��ռ䣻
* outline��һ���Ǿ��Ρ�

### ��������˵��
```css
/* ��������ɫ 
 * invert��ʾΪ��ɫ��ת����ʹ�����ڲ�ͬ�ı�����ɫ�ж��ɼ� 
 */
outline-color: invert | <color_name> | <hex_number> | <rgb_number> | inherit
/* ��������ʽ */
outline-style: none | dotted | dashed | solid | double | groove | ridge | inset | outset | inherit
/* �����߿�� */
outline-width: medium | thin | thick | <length> | inherit
/* һ�������������ߵ���ɫ����ʽ �� ��� */
outline: <outline-color> <outline-style> <outline-width>;
/* �����ߵ�ƫ����������0����������С��0��������С */
outline-offset: 0px;
```

## ħ����ϸ��
### ������
* `outline`��Ϊ**CSS2.1�淶**�����**IE6/7/8(Q)����֧��**����IE8��д����ȷ��DOCTYPE��֧��`outline`���ԡ�
* `outline-offset`��**IE�¾���֧��**��

### IE6/7/8(Q)������outline
��Ҫ��**IE6/7/8(Q)**������`outline`Ч��������Ԫ�������`hideFocus`���Լ��ɡ�

### outline:0��outline:none������
��Chrome��ִ�����´���
```html
<style type="text/css">
 .outline0{
   outline: 0;
 }
 .outline-none{
   outline: none;
 }
</style>
<a href="#" class="outline0">outline: 0</a>
<a href="#" class="outline-none">outline: none</a>
<script type="text/javascript">
  const $ = document.querySelector.bind(document)
  const print = console.log.bind(console)
  const cssProps = ["outline-width", "outline-style", "outline-color"]
  const slctrs = [".outline0", ".outline-none"]
     
  slctrs.forEach(slctr => {
    styles = window.getComputedStyle($(slctr))
      cssProps.forEach(cssProp => {
        print("%s, %s is %s", slctr, cssProp, styles[cssProp])
      })
    })
</script>
```

**���**��
```css
.outline0, outline-width is 0px
.outline0, outline-style is none
.outline0, outline-color is rgb(0, 0, 238)
.outline-none, outline-width is 0px
.outline-none, outline-style is none
.outline-none, outline-color is rgb(0, 0, 238)
```
`outline`����Ϊ���õ������������`outline`�����ṩ����ݵ�API���ѣ����`outline:0`��`outline:none`������Ч����һ�µġ�

### ����û��Ū��Բ��
�Դ�����`border-radius`�����ǾͿ���ͨ��CSS����Բ�Ǿ��Ρ�Բ�ε�ͼ�Σ�������`box-shadow`Ҳ�ܵ�`border-radius`Ӱ��Ӷ�ʵ��Ԫ����ӰҲ������Բ�ǵ�Ч������ô`outline`�Ƿ�Ҳ������Բ�ǵ�Ч���أ�  

���Ƿ񶨵ġ�������Ϊ`outline`�����ñ����������ڹ��ճ�Ԫ����ռ�Ŀռ�������ͨ��`border-radius`��Ȼʵ����ͼ���Ӿ��ϵ�Բ�ǣ�����Ԫ����ռλ�ÿռ�һ�㶼û�б仯�������Ǹ������нǵķ��Ρ�
```html
<style type="text/css">
  .round{
    width: 100px;
    height: 100px;
    background: yellow;
    border-radius: 50%;
    outline: solid 1px red;
  }
</style>
```

![img1](http://p3nqtyvgo.bkt.clouddn.com/2018100901.png)

### �����Ĳ���
?��Chrome��outline�����ڱ�ʶ��ǰԪ��������ռ��λ�ÿռ䣨border-box��������FireFox�����������Ԫ����ռ��λ�ÿռ䡣
```html
<style type="text/css">
  .outline{
    width: 13px;
    height: 13px;
    outline: 1px solid red;
  }
</style>
<div class="outline"></div>
<script type="text/javascript">
  const el = document.querySelector(".outline")
  el.textContent = !!~navigator.appVersion.indexOf("Chrome") ? "Chrome" : "FireFox"
</script>
```

![img2](http://p3nqtyvgo.bkt.clouddn.com/2018100902png.png)