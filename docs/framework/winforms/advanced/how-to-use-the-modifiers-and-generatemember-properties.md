---
title: Como usar os modificadores e as propriedades GenerateMember
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f11595daac74ceb76c5d017af015d5523506bdf3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a><span data-ttu-id="72649-102">Como usar os modificadores e as propriedades GenerateMember</span><span class="sxs-lookup"><span data-stu-id="72649-102">How to: Use the Modifiers and GenerateMember Properties</span></span>
<span data-ttu-id="72649-103">Quando você coloca um componente em um Windows Form, duas propriedades são fornecidas pelo ambiente de design: `GenerateMember` e `Modifiers`.</span><span class="sxs-lookup"><span data-stu-id="72649-103">When you place a component on a Windows Form, two properties are provided by the design environment: `GenerateMember` and `Modifiers`.</span></span> <span data-ttu-id="72649-104">A propriedade `GenerateMember` especifica quando o Designer de Formulários do Windows gera uma variável de membro de um componente.</span><span class="sxs-lookup"><span data-stu-id="72649-104">The `GenerateMember` property specifies when the Windows Forms Designer generates a member variable for a component.</span></span> <span data-ttu-id="72649-105">A propriedade `Modifiers` é o modificador de acesso atribuído a essa variável de membro.</span><span class="sxs-lookup"><span data-stu-id="72649-105">The `Modifiers` property is the access modifier assigned to that member variable.</span></span> <span data-ttu-id="72649-106">Se o valor da propriedade `GenerateMember` for `false`, o valor da propriedade `Modifiers` não terá efeito.</span><span class="sxs-lookup"><span data-stu-id="72649-106">If the value of the `GenerateMember` property is `false`, the value of the `Modifiers` property has no effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72649-107">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="72649-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="72649-108">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="72649-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="72649-109">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="72649-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a><span data-ttu-id="72649-110">Para especificar se um componente é um membro do formulário</span><span class="sxs-lookup"><span data-stu-id="72649-110">To specify whether a component is a member of the form</span></span>  
  
1.  <span data-ttu-id="72649-111">No Designer de Formulários do Windows, abra o formulário.</span><span class="sxs-lookup"><span data-stu-id="72649-111">In the Windows Forms Designer, open your form.</span></span>  
  
2.  <span data-ttu-id="72649-112">Abra o **caixa de ferramentas**e no formulário, coloque três <xref:System.Windows.Forms.Button> controles.</span><span class="sxs-lookup"><span data-stu-id="72649-112">Open the **Toolbox**, and on the form, place three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
3.  <span data-ttu-id="72649-113">Definir o `GenerateMember` e `Modifiers` propriedades para cada <xref:System.Windows.Forms.Button> controle de acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="72649-113">Set the `GenerateMember` and `Modifiers` properties for each <xref:System.Windows.Forms.Button> control according to the following table.</span></span>  
  
    |<span data-ttu-id="72649-114">Nome do botão</span><span class="sxs-lookup"><span data-stu-id="72649-114">Button name</span></span>|<span data-ttu-id="72649-115">Valor GenerateMember</span><span class="sxs-lookup"><span data-stu-id="72649-115">GenerateMember value</span></span>|<span data-ttu-id="72649-116">Valor de modificadores</span><span class="sxs-lookup"><span data-stu-id="72649-116">Modifiers value</span></span>|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|<span data-ttu-id="72649-117">Nenhuma alteração</span><span class="sxs-lookup"><span data-stu-id="72649-117">No change</span></span>|  
  
4.  <span data-ttu-id="72649-118">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="72649-118">Build the solution.</span></span>  
  
5.  <span data-ttu-id="72649-119">Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.</span><span class="sxs-lookup"><span data-stu-id="72649-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
6.  <span data-ttu-id="72649-120">Abra o nó **Form1** e no **Editor de Códigos**, abra o arquivo **Form1.Designer.vb** ou **Form1. Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="72649-120">Open the **Form1** node, and in the **Code Editor**,open the **Form1.Designer.vb** or **Form1.Designer.cs** file.</span></span> <span data-ttu-id="72649-121">Esse arquivo contém o código emitido pelo Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="72649-121">This file contains the code emitted by the Windows Forms Designer.</span></span>  
  
7.  <span data-ttu-id="72649-122">Localize as declarações dos três botões.</span><span class="sxs-lookup"><span data-stu-id="72649-122">Find the declarations for the three buttons.</span></span> <span data-ttu-id="72649-123">O exemplo de código a seguir mostra as diferenças especificadas pelas propriedades `GenerateMember` e `Modifiers`.</span><span class="sxs-lookup"><span data-stu-id="72649-123">The following code example shows the differences specified by the `GenerateMember` and `Modifiers` properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  <span data-ttu-id="72649-124">Por padrão, o Windows Forms Designer atribui o `private` (`Friend` no Visual Basic) modificador para controles de contêiner, como <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="72649-124">By default, the Windows Forms Designer assigns the `private` (`Friend` in Visual Basic) modifier to container controls like <xref:System.Windows.Forms.Panel>.</span></span> <span data-ttu-id="72649-125">Se sua base de <xref:System.Windows.Forms.UserControl> ou <xref:System.Windows.Forms.Form> tem um controle de contêiner, ele não aceitará novos filhos em controles em formulários herdados.</span><span class="sxs-lookup"><span data-stu-id="72649-125">If your base <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Form> has a container control, it will not accept new children in inherited controls and forms.</span></span> <span data-ttu-id="72649-126">A solução é alterar o modificador da caixa de controles de base para `protected` ou `public`.</span><span class="sxs-lookup"><span data-stu-id="72649-126">The solution is to change the modifier of the base container control to `protected` or `public`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72649-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72649-127">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="72649-128">Herança Visual dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="72649-128">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [<span data-ttu-id="72649-129">Instruções passo a passo: demonstrando herança visual</span><span class="sxs-lookup"><span data-stu-id="72649-129">Walkthrough: Demonstrating Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 [<span data-ttu-id="72649-130">Como Herdar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="72649-130">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)
