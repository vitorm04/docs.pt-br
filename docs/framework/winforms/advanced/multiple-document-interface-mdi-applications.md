---
title: Aplicativos de Interface de Documentos Múltiplos (MDI)
description: Saiba como Windows Forms aplicativos de MDI (interface de vários documentos) permitem que você exiba vários documentos ao mesmo tempo, com cada documento exibido em sua própria janela.
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0912a989ac1710d72c9db1cceb0e695f0ca85dee
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174647"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="e568f-103">Aplicativos de Interface de Documentos Múltiplos (MDI)</span><span class="sxs-lookup"><span data-stu-id="e568f-103">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="e568f-104">Aplicativos de interface de documentos múltiplos (MDI) permitem que você exiba vários documentos ao mesmo tempo, com cada documento exibido em sua própria janela.</span><span class="sxs-lookup"><span data-stu-id="e568f-104">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="e568f-105">Aplicativos MDI geralmente têm um item de menu de Janela com submenus para alternar entre janelas ou documentos.</span><span class="sxs-lookup"><span data-stu-id="e568f-105">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e568f-106">Existem algumas diferenças de comportamento entre formulários MDI e janelas da interface de documento único (SDI) nos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e568f-106">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="e568f-107">A propriedade `Opacity` não afeta a aparência dos formulários filho MDI.</span><span class="sxs-lookup"><span data-stu-id="e568f-107">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="e568f-108">Além disso, o <xref:System.Windows.Forms.Form.CenterToParent%2A> método não afeta o comportamento de formulários filho MDI.</span><span class="sxs-lookup"><span data-stu-id="e568f-108">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e568f-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e568f-109">In This Section</span></span>  
 [<span data-ttu-id="e568f-110">Como criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="e568f-110">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="e568f-111">Fornece instruções para criar o contêiner para diversos documentos em um aplicativo MDI.</span><span class="sxs-lookup"><span data-stu-id="e568f-111">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="e568f-112">Como criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="e568f-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="e568f-113">Fornece instruções de como criar uma ou mais janelas que operam em um formulário pai MDI.</span><span class="sxs-lookup"><span data-stu-id="e568f-113">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="e568f-114">Como determinar o filho MDI ativo</span><span class="sxs-lookup"><span data-stu-id="e568f-114">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="e568f-115">Fornece instruções de como verificar a janela filho que tem o foco (e enviar seu conteúdo para a área de transferência).</span><span class="sxs-lookup"><span data-stu-id="e568f-115">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="e568f-116">Como enviar dados para o filhos MDI ativos</span><span class="sxs-lookup"><span data-stu-id="e568f-116">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="e568f-117">Fornece instruções de como transportar informações para a janela filho ativa.</span><span class="sxs-lookup"><span data-stu-id="e568f-117">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="e568f-118">Como Organizar Formulários Filho MDI</span><span class="sxs-lookup"><span data-stu-id="e568f-118">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="e568f-119">Fornece instruções de como organizar lado a lado, em cascata ou organizar as janelas filho de um aplicativo MDI.</span><span class="sxs-lookup"><span data-stu-id="e568f-119">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
