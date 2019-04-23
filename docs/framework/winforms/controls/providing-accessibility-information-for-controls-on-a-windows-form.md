---
title: Fornecendo informações de acessibilidade para controles em um Windows Form
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: 0f589f37d79c9ec8d55153aac4c846726a379055
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218323"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a>Fornecendo informações de acessibilidade para controles em um Windows Form
Os recursos de acessibilidade são programas e dispositivos especializados que ajudam as pessoas com deficiência a usarem computadores de forma mais eficaz. Alguns exemplos incluem leitores de tela para pessoas cegas e utilitários de entrada de voz para as pessoas que fornecem comandos verbais em vez de usar o mouse ou teclado. Esses recursos de acessibilidade interagem com as propriedades de acessibilidade expostas pelos controles dos Windows Forms. Essas propriedades são:  
  
-   **AccessibilityObject**  
  
-   **AccessibleDefaultActionDescription**  
  
-   **AccessibleDescription**  
  
-   **AccessibleName**  
  
-   **AccessibleRole**  
  
## <a name="accessibilityobject-property"></a>Propriedade AccessibilityObject  
 Esta propriedade somente leitura contém um <xref:System.Windows.Forms.AccessibleObject> instância. O **AccessibleObject** implementa o <xref:Accessibility.IAccessible> interface, que fornece informações sobre o controle de descrição, local da tela, recursos de navegação e valor. O designer define esse valor quando o controle é adicionado ao formulário.  
  
## <a name="accessibledefaultactiondescription-property"></a>Propriedade AccessibleDefaultActionDescription  
 Essa cadeia de caracteres descreve as ações do controle. Ela não aparece na janela Propriedades e só pode ser definido no código. O exemplo a seguir define essa propriedade para um controle de botão:  
  
```  
' Visual Basic  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
  
// C#  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
  
// C++  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a>Propriedade AccessibleDescription  
 Essa cadeia de caracteres descreve o controle. Ele pode ser definido na janela Propriedades ou no código da seguinte maneira:  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a>Propriedade AccessibleName  
 Esse é o nome de um controle relatado para os recursos de acessibilidade. Ele pode ser definido na janela Propriedades ou no código da seguinte maneira:  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a>Propriedade AccessibleRole  
 Essa propriedade, que contém um <xref:System.Windows.Forms.AccessibleRole> enumeração, descreve a função de interface do usuário do controle. Um novo controle tem o valor definido como `Default`. Isso significa que, por padrão, um controle **Botão** atua como um **Botão**. Pode ser útil redefinir essa propriedade se um controle tiver outra função. Por exemplo, você pode estar usando um controle **PictureBox** como um **Gráfico** e pode desejar que os recursos de acessibilidade relatem a função como um **Gráfico**, não como **PictureBox**. Também pode ser útil especificar essa propriedade para controles personalizados desenvolvidos por você. Essa propriedade pode ser definida na janela Propriedades ou no código da seguinte maneira:  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
