---
layout: post
title: Diagram Methods in Blazor Diagram Component | Syncfusion
description: Checkout and learn here all about Diagram Methods in Syncfusion Blazor Diagram component and much more.
platform: Blazor
control: DiagramComponent
documentation: ug
---

# Diagram Methods in Blazor Diagram Component

The following methods are used to perform the diagram functionalities.

## Add nodes through AddDiagramElements

The Add method is synchronous, so the call moves on to process the connections before processing the nodes internally. So, it is better to use [AddDiagramElements](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Diagram.SfDiagramComponent.html#Syncfusion_Blazor_Diagram_SfDiagramComponent_AddDiagramElements_Syncfusion_Blazor_Diagram_DiagramObjectCollection_Syncfusion_Blazor_Diagram_NodeBase__) method instead of the Add method to add nodes and connections at runtime.


```cshtml
@using Syncfusion.Blazor.Diagram

<button @onclick="Test">Test</button>

<SfDiagramComponent @ref="Diagram" Width="1000px" Height="500px">
</SfDiagramComponent>

@code
{
    SfDiagramComponent Diagram;

    public async void Test()
    {
        Node node1 = new Node()
        {
            OffsetX = 100,
            OffsetY = 100,
            Height = 50,
            Ports = new DiagramObjectCollection<PointPort>()
                {
                    new PointPort()
                    {
                        ID="port1",
                        Visibility = PortVisibility.Visible,
                        Offset = new DiagramPoint() { X = 1, Y = 0.5},
                        Height = 10, Width = 10,
                        Style = new ShapeStyle(){Fill = "yellow", StrokeColor = "yellow"}
                    }
                },
            Width = 100,
            ID = "node1",
            Style = new ShapeStyle() { Fill = "#6495ED", StrokeColor = "#6495ED" },
            Shape = new BasicShape() { Type = Shapes.Basic, Shape = BasicShapeType.Rectangle            }
        };
 
        Node node2 = new Node()
        {
            OffsetX = 300,
            OffsetY = 300,
            Height = 50,
            Width = 100,
            ID = "node2",
            Ports = new DiagramObjectCollection<PointPort>()
            {
                new PointPort()
                {
                    ID="port2",
                    Visibility = PortVisibility.Visible,
                    Offset = new DiagramPoint() { X = 0, Y = 0.5},
                    Height = 10, Width = 10,
                    Style = new ShapeStyle(){Fill = "yellow", StrokeColor = "yellow"}
               }
            },
            Style = new ShapeStyle() { Fill = "#6495ED", StrokeColor = "#6495ED" },
            Shape = new BasicShape() { Type = Shapes.Basic, Shape = BasicShapeType.Rectangle }
        };

        Connector Connector = new Connector()
        {
            ID = "connector1",
            //Source node id of the connector.
            SourceID = "node1",
            //source node port id.
            SourcePortID = "port1",
            //Target node id of the connector.
            TargetID = "node2",
            //Target node port id.
            TargetPortID = "port2",
            TargetDecorator = new DecoratorSettings()
            {
                Style = new ShapeStyle()
                {
                    Fill = "#6495ED",
                    StrokeColor = "#6495ED",
                }
            },
            Style = new ShapeStyle()
            {
                Fill = "#6495ED",
                StrokeColor = "#6495ED",
            },
            // Type of the connector
            Type = ConnectorSegmentType.Straight,
        };
        DiagramObjectCollection<NodeBase> NodeCollection = new DiagramObjectCollection<NodeBase>();
        NodeCollection.Add(node1);
        NodeCollection.Add(node2);
        NodeCollection.Add(Connector);
        await Diagram.AddDiagramElements(NodeCollection);
    }
}
```
