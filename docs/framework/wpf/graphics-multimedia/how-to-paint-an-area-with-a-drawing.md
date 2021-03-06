---
title: 'Cómo: Pintar un área con un dibujo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
ms.openlocfilehash: 222aa3fbb72ebaf15be3ed7f9804936e7e1187e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-paint-an-area-with-a-drawing"></a>Cómo: Pintar un área con un dibujo
En este ejemplo se muestra cómo pintar un área con un dibujo. Para pintar un área con un dibujo, use un <xref:System.Windows.Media.DrawingBrush> y uno o más <xref:System.Windows.Media.Drawing> objetos.   En el ejemplo siguiente se usa un <xref:System.Windows.Media.DrawingBrush> para pintar un objeto con un dibujo de dos elipses.  
  
## <a name="example"></a>Ejemplo  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 En la siguiente ilustración se muestra el resultado del ejemplo.  
  
 ![Resultado de DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")  
  
 (El centro de la forma es blanco por las razones descritas en [controlar el relleno de una forma compuesta](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-the-fill-of-a-composite-shape.md).)  
  
 Estableciendo un <xref:System.Windows.Media.DrawingBrush> del objeto <xref:System.Windows.Media.TileBrush.Viewport%2A> y <xref:System.Windows.Media.TileBrush.TileMode%2A> propiedades, puede crear un patrón de repetición. En el ejemplo siguiente se pinta un objeto con un patrón creado a partir de un dibujo de dos elipses.  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 La siguiente ilustración muestra el mosaico <xref:System.Windows.Media.DrawingBrush> salida.  
  
 ![Resultado en mosaico de DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")  
  
 Para obtener más información sobre pinceles de dibujo, consulte [pintar con imágenes, gráficos y objetos visuales](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md). Para obtener más información acerca de <xref:System.Windows.Media.Drawing> los objetos, vea la [información general de objetos de dibujo](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).
