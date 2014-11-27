jquery.searchHistory.js
=======================

a jquery plugin showing the search history on the html's input element, and some operations are added to it, and can cooperate with jquery.autocompleter.js created by ArtemFitiskin.

script:
-------
    script(type='text/javascript',src='jquery.js')
    //need this jquery plugin to support cookie operations
    script(type='text/javascript',src='jquery.cookie.js')
    script(type='text/javascript',src='jquery.searchHistory.js')

styles:
--------
    //in demo, this style is written by less, and some other styles don't matter much
    link(rel='stylesheet',type='text/css',href='jquery.searchHistory.css')

Define your searchHistory:
--------------------------
    //be carefull, this plugin's performance is showed on input element
    //but declared on form element.
    //I do so, just wannait can work with jquery.autocompleter.js created by ArtemFitiskin 
    $(function () {
      $('#historyForm').searchHistory({expires:7});
    });

Options:
---------------
<table>
<thead>
<tr>
<th>Name</th>
<th align="center">Type</th>
<th align="right">Description</th>
<th align="right">Deafult</th>
</tr>
</thead>
<tbody>
<tr>
<td>maxShowNum</td>
<td align="center">number</td>
<td align="right">the number of the search history showing on screen</td>
<td align="right">4</td>
</tr>
<tr>
<td>expires</td>
<td align="center">number</td>
<td align="right">cookies' expires, day as the basic unit</td>
<td align="right">7</td>
</tr>
<tr>
<td>input</td>
<td align="center">string</td>
<td align="right">the jquery selector for input element</td>
<td align="right">'.history-input'</td>
</tr>
<tr>
<td>cookiesName</td>
<td align="center">string</td>
<td align="right">the name of cookie</td>
<td align="right">'searchHistory'</td>
</tr>
<tr>
<td>selected</td>
<td align="center">function(value)</td>
<td align="right">triggered after an item is selected, and the selected value will ed transfered</td>
<td align="right">doing nothing</td>
</tr>
<tr>
<td>beforeSend</td>
<td align="center">function(value)</td>
<td align="right">triggered before submiting the form, and the submiting value will be transformed</td>
<td align="right">doing nothing</td>
</tr>
<tr>
<td>sendWhenSelected</td>
<td align="center">bool</td>
<td align="right">submit the form when an item is selected</td>
<td align="right">true</td>
</tr>
<tr>
<td>actionByCall</td>
<td align="center">bool</td>
<td align="right">are the performances of this plugin triggered by call, for cooperating with other plugins </td>
<td align="right">false</td>
</tr>
</tbody>
</table>

Methods:
--------
### open list
    $('.historyForm').searchHistory('open')

### close list
    $('.historyForm').searchHistory('close')
    
### clear history
    $('.historyForm').searchHistory('clear')
    
    
Example:
===========

Form:
------
	  .row
		.col-xs-10.col-xs-offset-5
			form#historyForm(action='',method='POST')
				.form-control-group
					input.history-input.form-control(type='text',placeholder='input')
				.row.height-10
				.row
					button#open(type='button').btn.btn-primary open
					p
					button#close(type='button').btn.btn-info close
					p
					button#clear(type='button').btn.btn-warning clear
					
					
JavaScript:
------------
    $(function(){
			$('#historyForm').searchHistory({
				'sendWhenSelect':false,
				//you can set 'actionByCall' to false and experience the differences
				'actionByCall':true
			});
			$('#open').click(function(){$('#historyForm').searchHistory('open');});
			$('#close').click(function(){$('#historyForm').searchHistory('close');});
			$('#clear').click(function(){$('#historyForm').searchHistory('clear');});
		});

