---
title: "EventStack class"
description: "The C++ Build Insights SDK EventStack class reference."
ms.date: "02/12/2020"
helpviewer_keywords: ["C++ Build Insights", "C++ Build Insights SDK", "EventStack", "throughput analysis", "build time analysis", "vcperf.exe"]
---
# EventStack class

::: moniker range="<=vs-2015"

The C++ Build Insights SDK is compatible with Visual Studio 2017 and above. To see the documentation for these versions, set the Visual Studio version selector control for this article to Visual Studio 2017 or Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

The `EventStack` class is a collection of [Event](event.md) objects. All events received from the C++ Build Insights SDK come in the form of an `EventStack` object. The last entry in this stack is the event currently being processed. The entries that precede the last entry are the parent hierarchy of the current event. For more information on the event model used in C++ Build Insights, see [event table](../event-table.md).

## Syntax

```cpp
class EventStack
{
public:
    EventStack(const EVENT_COLLECTION_DATA& data);

    size_t      Size() const;
    RawEvent    Back() const;
    RawEvent    operator[] (size_t index) const;
};
```

## Members

### Constructors

[EventStack](#event-stack)

### Functions

[Back](#back)
[operator[]](#subscript-operator)
[Size](#size)

## <a name="back"></a> Back

```cpp
RawEvent Back() const;
```

### Return Value

A [RawEvent](raw-event.md) object that represents the last entry in the stack. The last entry in an event stack is the event that was triggered.

## <a name="event-stack"></a> EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### Parameters

*data*\
The raw data from which the `EventStack` is built.

### Remarks

You don't typically need to construct `EventStack` objects yourself. They're provided to you by the C++ Build Insights SDK when events are being processed during an analysis or relogging session.

## <a name="subscript-operator"></a> operator[]

```cpp
RawEvent operator[] (size_t index) const;
```

### Parameters

*index*\
The index of the element to access in the event stack.

### Return Value

A [RawEvent](raw-event.md) object that represents the event stored at the position indicated by *index* in the event stack.

## <a name="size"></a> Size

```cpp
size_t Size() const;
```

### Return Value

The size of the event stack.

::: moniker-end
