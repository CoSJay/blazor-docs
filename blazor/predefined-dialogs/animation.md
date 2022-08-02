---
layout: post
title: Animation in Blazor Predefined Dialogs Component | Syncfusion
description: Checkout and learn here all about animation in Syncfusion Blazor Predefined Dialogs component and much more details.
platform: Blazor
control: Predefined Dialogs
documentation: ug
---

# Animation in Blazor Predefined Dialogs Component

The Predefined Dialogs can be animated during the open and close actions. Also, users can customize animation’s `Delay`, `Duration`, and `Effect` by using the [DialogOptions.AnimationSettings](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Popups.DialogOptions.html#Syncfusion_Blazor_Popups_DialogOptions_AnimationSettings) property.

In the following sample, the `Zoom` effect is enabled. So, the Dialog will open with the `ZoomIn` and close with the `ZoomOut` effects.

{% tabs %}

{% highlight razor tabtitle="alert.razor" %}
{% include_relative code-snippet/alert-animation.razor %}
{% endhighlight %}

{% highlight razor tabtitle="confirm.razor" %}
{% include_relative code-snippet/confirm-animation.razor %}
{% endhighlight %}

{% highlight razor tabtitle="prompt.razor" %}
{% include_relative code-snippet/prompt-animation.razor %}
{% endhighlight %}

{% endtabs %}