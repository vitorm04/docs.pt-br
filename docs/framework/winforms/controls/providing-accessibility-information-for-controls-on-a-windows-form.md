---
title: Fornecendo informações de acessibilidade para controles em um Windows Form
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: 3067c90978e6ebd680d10c1c4f9db131f19c9e44
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614751"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a><span data-ttu-id="9eb67-102">Fornecendo informações de acessibilidade para controles em um Windows Form</span><span class="sxs-lookup"><span data-stu-id="9eb67-102">Providing Accessibility Information for Controls on a Windows Form</span></span>
<span data-ttu-id="9eb67-103">Os recursos de acessibilidade são programas e dispositivos especializados que ajudam as pessoas com deficiência a usarem computadores de forma mais eficaz.</span><span class="sxs-lookup"><span data-stu-id="9eb67-103">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span> <span data-ttu-id="9eb67-104">Alguns exemplos incluem leitores de tela para pessoas cegas e utilitários de entrada de voz para as pessoas que fornecem comandos verbais em vez de usar o mouse ou teclado.</span><span class="sxs-lookup"><span data-stu-id="9eb67-104">Examples include screen readers for people who are blind and voice input utilities for people who provide verbal commands instead of using the mouse or keyboard.</span></span> <span data-ttu-id="9eb67-105">Esses recursos de acessibilidade interagem com as propriedades de acessibilidade expostas pelos controles dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9eb67-105">These accessibility aids interact with the accessibility properties exposed by Windows Forms controls.</span></span> <span data-ttu-id="9eb67-106">Essas propriedades são:</span><span class="sxs-lookup"><span data-stu-id="9eb67-106">These properties are:</span></span>  
  
- <span data-ttu-id="9eb67-107">**AccessibilityObject**</span><span class="sxs-lookup"><span data-stu-id="9eb67-107">**AccessibilityObject**</span></span>  
  
- <span data-ttu-id="9eb67-108">**AccessibleDefaultActionDescription**</span><span class="sxs-lookup"><span data-stu-id="9eb67-108">**AccessibleDefaultActionDescription**</span></span>  
  
- <span data-ttu-id="9eb67-109">**AccessibleDescription**</span><span class="sxs-lookup"><span data-stu-id="9eb67-109">**AccessibleDescription**</span></span>  
  
- <span data-ttu-id="9eb67-110">**AccessibleName**</span><span class="sxs-lookup"><span data-stu-id="9eb67-110">**AccessibleName**</span></span>  
  
- <span data-ttu-id="9eb67-111">**AccessibleRole**</span><span class="sxs-lookup"><span data-stu-id="9eb67-111">**AccessibleRole**</span></span>  
  
## <a name="accessibilityobject-property"></a><span data-ttu-id="9eb67-112">Propriedade AccessibilityObject</span><span class="sxs-lookup"><span data-stu-id="9eb67-112">AccessibilityObject Property</span></span>  
 <span data-ttu-id="9eb67-113">Esta propriedade somente leitura contém um <xref:System.Windows.Forms.AccessibleObject> instância.</span><span class="sxs-lookup"><span data-stu-id="9eb67-113">This read-only property contains an <xref:System.Windows.Forms.AccessibleObject> instance.</span></span> <span data-ttu-id="9eb67-114">O **AccessibleObject** implementa o <xref:Accessibility.IAccessible> interface, que fornece informações sobre o controle de descrição, local da tela, recursos de navegação e valor.</span><span class="sxs-lookup"><span data-stu-id="9eb67-114">The **AccessibleObject** implements the <xref:Accessibility.IAccessible> interface, which provides information about the control's description, screen location, navigational abilities, and value.</span></span> <span data-ttu-id="9eb67-115">O designer define esse valor quando o controle é adicionado ao formulário.</span><span class="sxs-lookup"><span data-stu-id="9eb67-115">The designer sets this value when the control is added to the form.</span></span>  
  
## <a name="accessibledefaultactiondescription-property"></a><span data-ttu-id="9eb67-116">Propriedade AccessibleDefaultActionDescription</span><span class="sxs-lookup"><span data-stu-id="9eb67-116">AccessibleDefaultActionDescription Property</span></span>  
 <span data-ttu-id="9eb67-117">Essa cadeia de caracteres descreve as ações do controle.</span><span class="sxs-lookup"><span data-stu-id="9eb67-117">This string describes the action of the control.</span></span> <span data-ttu-id="9eb67-118">Ela não aparece na janela Propriedades e só pode ser definido no código.</span><span class="sxs-lookup"><span data-stu-id="9eb67-118">It does not appear in the Properties window and may only be set in code.</span></span> <span data-ttu-id="9eb67-119">O exemplo a seguir define essa propriedade para um controle de botão:</span><span class="sxs-lookup"><span data-stu-id="9eb67-119">The following example sets this property for a button control:</span></span>  
  
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
  
## <a name="accessibledescription-property"></a><span data-ttu-id="9eb67-120">Propriedade AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="9eb67-120">AccessibleDescription Property</span></span>  
 <span data-ttu-id="9eb67-121">Essa cadeia de caracteres descreve o controle.</span><span class="sxs-lookup"><span data-stu-id="9eb67-121">This string describes the control.</span></span> <span data-ttu-id="9eb67-122">Ele pode ser definido na janela Propriedades ou no código da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9eb67-122">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a><span data-ttu-id="9eb67-123">Propriedade AccessibleName</span><span class="sxs-lookup"><span data-stu-id="9eb67-123">AccessibleName Property</span></span>  
 <span data-ttu-id="9eb67-124">Esse é o nome de um controle relatado para os recursos de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="9eb67-124">This is the name of a control reported to accessibility aids.</span></span> <span data-ttu-id="9eb67-125">Ele pode ser definido na janela Propriedades ou no código da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9eb67-125">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a><span data-ttu-id="9eb67-126">Propriedade AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="9eb67-126">AccessibleRole Property</span></span>  
 <span data-ttu-id="9eb67-127">Essa propriedade, que contém um <xref:System.Windows.Forms.AccessibleRole> enumeração, descreve a função de interface do usuário do controle.</span><span class="sxs-lookup"><span data-stu-id="9eb67-127">This property, which contains an <xref:System.Windows.Forms.AccessibleRole> enumeration, describes the user interface role of the control.</span></span> <span data-ttu-id="9eb67-128">Um novo controle tem o valor definido como `Default`.</span><span class="sxs-lookup"><span data-stu-id="9eb67-128">A new control has the value set to `Default`.</span></span> <span data-ttu-id="9eb67-129">Isso significa que, por padrão, um controle **Botão** atua como um **Botão**.</span><span class="sxs-lookup"><span data-stu-id="9eb67-129">This would mean that by default, a **Button** control acts as a **Button**.</span></span> <span data-ttu-id="9eb67-130">Pode ser útil redefinir essa propriedade se um controle tiver outra função.</span><span class="sxs-lookup"><span data-stu-id="9eb67-130">You may want to reset this property if a control has another role.</span></span> <span data-ttu-id="9eb67-131">Por exemplo, você pode estar usando um controle **PictureBox** como um **Gráfico** e pode desejar que os recursos de acessibilidade relatem a função como um **Gráfico**, não como **PictureBox**.</span><span class="sxs-lookup"><span data-stu-id="9eb67-131">For example, you may be using a **PictureBox** control as a **Chart**, and you may want accessibility aids to report the role as a **Chart**, not as a **PictureBox**.</span></span> <span data-ttu-id="9eb67-132">Também pode ser útil especificar essa propriedade para controles personalizados desenvolvidos por você.</span><span class="sxs-lookup"><span data-stu-id="9eb67-132">You may also want to specify this property for custom controls you have developed.</span></span> <span data-ttu-id="9eb67-133">Essa propriedade pode ser definida na janela Propriedades ou no código da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9eb67-133">This property may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a><span data-ttu-id="9eb67-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9eb67-134">See also</span></span>

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
