---
title: 'Cómo: Ver múltiples líneas en el control TextBox de formularios Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
ms.openlocfilehash: c826a519d8be05430eb6e2434209424514347b5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Cómo: Ver múltiples líneas en el control TextBox de formularios Windows Forms
De forma predeterminada, los formularios Windows Forms <xref:System.Windows.Forms.TextBox> control muestra una sola línea de texto y no muestra barras de desplazamiento. Si el texto es más largo que el espacio disponible, solo una parte del texto está visible. Puede cambiar este comportamiento predeterminado estableciendo la <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, y <xref:System.Windows.Forms.TextBox.ScrollBars%2A> propiedades en los valores adecuados.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>Para mostrar un retorno de carro en el control de cuadro de texto  
  
-   Para mostrar un retorno de carro en una de varias líneas <xref:System.Windows.Forms.TextBox>, use el <xref:System.Environment.NewLine%2A> propiedad.  
  
     Tenga en cuenta que la interpretación de caracteres de escape (\\) es específico del idioma. Visual Basic usa `Chr$(13) & Chr$(10)` para la combinación de caracteres de retorno de carro y de transporte.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>Para ver varias líneas en el control de cuadro de texto  
  
1.  Establezca la propiedad <xref:System.Windows.Forms.TextBox.Multiline%2A> en `true`. Si <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> es `true` (valor predeterminado), a continuación, el texto en el control se mostrará como uno o varios párrafos; en caso contrario, aparecerá como una lista, en el que algunas líneas pueden quedar cortadas en el borde del control.  
  
2.  Establezca la propiedad <xref:System.Windows.Forms.TextBox.ScrollBars%2A> en un valor apropiado.  
  
    |Valor|Descripción|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Utilice este valor si el texto será un párrafo que casi siempre se ajusta el control. El usuario puede utilizar el puntero del mouse para moverse por el control si el texto es demasiado largo para mostrarse a la vez.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Use este valor si desea mostrar una lista de líneas, algunas de las cuales pueden ser mayor que el ancho de la <xref:System.Windows.Forms.TextBox> control.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Utilice este valor si la lista puede ser mayor que el alto del control.|  
  
3.  Establezca la propiedad <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> en un valor apropiado.  
  
    |Valor|Descripción|  
    |-----------|-----------------|  
    |`false`|Texto en el control no automáticamente se ajustará, por lo que se desplazará a la derecha hasta que se alcance un salto de línea. Utilice este valor si eligió <xref:System.Windows.Forms.ScrollBars.Horizontal> las barras de desplazamiento o <xref:System.Windows.Forms.ScrollBars.Both>anteriormente.|  
    |`true` (valor predeterminado)|No se mostrará la barra de desplazamiento horizontal. Utilice este valor si eligió <xref:System.Windows.Forms.ScrollBars.Vertical> las barras de desplazamiento o <xref:System.Windows.Forms.ScrollBars.None>, anterior, para mostrar uno o varios párrafos.|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Forms.TextBox>  
 [Información general sobre el control TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Controlar el punto de inserción en un control TextBox de Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Crear un cuadro de texto de contraseña con el control TextBox de Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Crear un cuadro de texto de sólo lectura](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Insertar comillas en una cadena](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Seleccionar texto en el control TextBox de Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Control TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
