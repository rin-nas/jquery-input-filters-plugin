# jQuery Input filters (multiple) plugin

Позволяет фильтровать ввод в текстовые поля ввода, используя маску ввода. Т.о. даёт ввести только разрешённые символы.

#Демо

http://jsfiddle.net/9rmf1Ljy/33/

#Пример использования

```javascript
$(function() {
	//фамилия, имя, отчество клиента
	$('input.person-name').inputFilter({
		filters : {
			//допускается ввод или только по-английски, или только по-русски
			en: [
				/^[a-zA-Z]+$/, 		//первый элемент массива используется для первого символа ввода
				/^[a-zA-Z\-']+$/	//второй элемент массива используется для второго и последующих символов ввода
			],
			ru: [/^[\u0410-\u044F\u0401\u0451]+$/, /^[\u0410-\u044F\u0401\u0451\-']+$/]
		}
	});
	//серия и номер документа, удостоверяющего личность
	$('input.doc-serial, input.doc-number').inputFilter({
		filters : {
			en: [/^[\da-zA-Z]+$/, /^[\da-zA-Z\- ]+$/],
			ru: [/^[\d\u0410-\u044F\u0401\u0451]+$/, /^[\d\u0410-\u044F\u0401\u0451\- ]+$/]
		}
	});
	//номер денежного перевода
	$('input.mt-number').inputFilter({
		filters : {
			xx: [/^[\da-zA-Z]+$/, /^[\da-zA-Z ]+$/]
		}
	});
	//номер телефона
	$('input[type=tel]').inputFilter({
		filters : {
			dd: [/^\d+$/, /^[\d\.\-() ]+$/]
		}
	});
	//номер карты клиента
	$('input.client-card, input.doc-issue-code').inputFilter({
		filters : {
			dd: [/^\d+$/, /^[\d\- ]+$/]
		}
	});
	//адрес электронной почты
	$('input[type=email]').inputFilter({
		filters : {
			en: /^[\x21-\x7e]+$/  //printable ASCII
		}
	});
	//поисковый запрос
	$('input[type=search]').inputFilter({
		filters : {
			en: [/^[\da-zA-Z]+$/, /^[\da-zA-Z\-' ]+$/],
			ru: [/^[\d\u0410-\u044F\u0401\u0451]+$/, /^[\d\u0410-\u044F\u0401\u0451\-' ]+$/]
		}
	});
	//дата (YYYY-MM-DD или DD.MM.YYYY)
	$('input[type=date]').inputFilter({
		filters : {
			dd: [/^\d+$/, /^[\d\.\-]+$/]
		}
	});
	//название страны, города
	$('input.country, input.city').inputFilter({
		filters : {
			en: [/^[a-zA-Z]+$/, /^[a-zA-Z\-'()\., ]+$/],
			ru: [/^[\u0410-\u044F\u0401\u0451]+$/, /^[\u0410-\u044F\u0401\u0451\-'()\., ]+$/]
		}
	});
	//сумма платежа
	$('input.money').inputFilter({
		filters : {
			dd: [/^\d+$/, /^[\d\.]+$/]
		}
	});
});
```
