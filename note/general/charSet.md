# 文字コード


## 目次

- [SHIFT-JIS と CP932](#ShiftJisVsCp932)


## <a id="ShiftJisVsCp932"></a> SHIFT-JIS と CP932

### 参考

- [Shift_JISとCP932とWindows-31Jの違いを整理した](https://monologu.com/sjis-cp932-windows31j/)

### SHIFT-JIS と CP932 の違い

- SHIFT-JIS

  JIS X 0208 で規格化されている文字符号化方式の一種

- CP932

  JIS X 0208 + 機種依存文字  
  Microsoft Windows 独自の文字符号化方式 (方法は SHIFT-JIS と同じ)  
  SHIFT-JIS のスーパーセット  

### CP932 と同じ文字コード

- Windows-31J

  IANA での登録名。  
  CP932 と同じ。  
  HTML などで文字コードを指定するときは、IANA に登録されている Windows-31J を使う必要がある。

- MS932

  JAVA において、IBM の CP932 と区別するために用意された名前。  
  CP932 と同じ。

