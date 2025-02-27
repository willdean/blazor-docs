---
title: Events
page_title: TimePicker for Blazor | Events
description: Events in the TimePicker for Blazor
slug: components/timepicker/events
tags: telerik,blazor,TimePicker,events
published: true
position: 20
---

# Events

This article explains the events available in the Telerik TimePicker for Blazor:

* [OnChange](#onchange)
* [ValueChanged](#valuechanged)

## OnChange

The `OnChange` event fires when the new value is commited by the user either by pressing `Enter`, or when the input loses focus.

The time picker is a generic component, so you must provide either a `Value`, or a type to the `T` parameter of the component.

>caption Handle OnChange

````CSHTML
@using Telerik.Blazor.Components.TimePicker

<TelerikTimePicker T="DateTime" OnChange="@MyOnChangeHandler"></TelerikTimePicker>

<br />
@result

@code {
    string result;

    private void MyOnChangeHandler(object theUserInput)
    {
        // the handler receives an object that you may need to cast to the type of the component
        // if you do not provide a Value, you must provide the Type parameter to the component
        result = string.Format("The user entered: {0:HH:mm:ss}", (DateTime)theUserInput);
    }
}
````

@[template](/_contentTemplates/common/general-info.md#event-callback-can-be-async)

>tip The `OnChange` event is a custom event and does not interfere with bindings, so you can use it together with models and forms.

>caption Handle OnChange and use two-way binding

````CSHTML
@using Telerik.Blazor.Components.TimePicker

<TelerikTimePicker @bind-Value="@thePickerValue" OnChange="@MyOnChangeHandler"></TelerikTimePicker>

<br />
@result
<br />
model value: @thePickerValue

@code {
    string result;

    DateTime? thePickerValue { get; set; } = DateTime.Now;

    private void MyOnChangeHandler(object theUserInput)
    {
        // the handler receives an object that you may need to cast to the type of the component
        // if you do not provide a Value, you must provide the Type parameter to the component
        result = string.Format("The user entered: {0}", (theUserInput as DateTime?).Value);
    }
}
````


## ValueChanged

The `ValueChanged` event fires upon every change (for example, keystroke) in the input, and upon clicking the `Set` or `Now` buttons in the dropdown.

>caption Handle ValueChanged

````CSHTML
@using Telerik.Blazor.Components.TimePicker

<TelerikTimePicker ValueChanged="@( (DateTime d) => MyValueChangeHandler(d) )"></TelerikTimePicker>

<br />
@result

@code {
    string result;

    private void MyValueChangeHandler(DateTime theUserInput)
    {
        result = string.Format("The user entered: {0}", theUserInput);
    }
}
````

@[template](/_contentTemplates/common/general-info.md#event-callback-can-be-async)

@[template](/_contentTemplates/common/issues-and-warnings.md#valuechanged-lambda-required)

>caption Handle ValueChanged and provide initial value

````CSHTML
@using Telerik.Blazor.Components.TimePicker

<TelerikTimePicker Value="@thePickerValue" ValueChanged="@( (DateTime d) => MyValueChangeHandler(d) )"></TelerikTimePicker>

<br />
@result
<br />
model value: @thePickerValue

@code {
    string result;

    DateTime thePickerValue { get; set; } = DateTime.Now;

    private void MyValueChangeHandler(DateTime theUserInput)
    {
        result = $"The user entered: {theUserInput}";

        //you have to update the model manually because handling the ValueChanged event does not let you use @bind-Value
        thePickerValue = theUserInput;
    }
}
````

## See Also

* [ValueChanged and Validation]({%slug value-changed-validation-model%})
