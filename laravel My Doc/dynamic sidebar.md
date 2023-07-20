#### Dynamic Sidebar with Javascript
```js
let path = window.location.href

path = path.replace('#', '')

let selector = "a[href='" + path + "']"

if (!$(selector).closest('li').hasClass('hasQuery')) {
    path = path.split('?')[0]
    selector = "a[href='" + path + "']"
}


if ($(selector).length < 1) {

    selector = selector.substring(0, selector.lastIndexOf('/'))

    if ($(selector).length < 1) {

        selector = selector.substring(0, selector.lastIndexOf('/'))

        if ($(selector).length < 1) {

            selector = selector.substring(0, selector.lastIndexOf('/'))

            if ($(selector).length < 1) {

                selector = selector.substring(0, selector.lastIndexOf('/'))
            }
        }
    }
}


let a_tag = $(selector)



let li_tag = a_tag.closest('li')

li_tag.addClass('active')

li_tag.parents('li').add(this).each(function() {

    $(this).addClass('open')

});



/*
 *--------------------------------------------------------------
 * DYNAMICALLY HANDLE SIDE MENU CHILDREN
 * DOM REMOVE IF DOES NOT HAVE ANY CHILDREN
 * ONLY WORKS IN NAVBAR ELEMENT
 *--------------------------------------------------------------
 */
$(document).on('ready', function() {
    $('.nav-list>li>ul').each(function() {


        $.each($(this).find('li>ul'), function() {

            $.each($(this).find('li>ul'), function() {


                if ($(this).children().length == 0) {
                    $(this).parent().remove()
                }
            })

            if ($(this).children().length == 0) {
                $(this).parent().remove()
            }
        })

        if ($(this).find('li').length == 0) {
            $(this).parent().remove()
        }

    })
})
```
