---
title: Aplicativos de Interface de Documentos Múltiplos (MDI)
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 23e0275d5e6b081ec02d669a78e8695453360637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956555"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="6d4ba-102">Aplicativos de Interface de Documentos Múltiplos (MDI)</span><span class="sxs-lookup"><span data-stu-id="6d4ba-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="6d4ba-103">Aplicativos de interface de documentos múltiplos (MDI) permitem que você exiba vários documentos ao mesmo tempo, com cada documento exibido em sua própria janela.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="6d4ba-104">Aplicativos MDI geralmente têm um item de menu de Janela com submenus para alternar entre janelas ou documentos.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d4ba-105">Existem algumas diferenças de comportamento entre formulários MDI e janelas da interface de documento único (SDI) nos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="6d4ba-106">A propriedade `Opacity` não afeta a aparência dos formulários filho MDI.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="6d4ba-107">Além disso, <xref:System.Windows.Forms.Form.CenterToParent%2A> o método não afeta o comportamento de formulários filho MDI.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d4ba-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6d4ba-108">In This Section</span></span>  
 [<span data-ttu-id="6d4ba-109">Como: Criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="6d4ba-109">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="6d4ba-110">Fornece instruções para criar o contêiner para diversos documentos em um aplicativo MDI.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="6d4ba-111">Como: Criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="6d4ba-111">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="6d4ba-112">Fornece instruções de como criar uma ou mais janelas que operam em um formulário pai MDI.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="6d4ba-113">Como: Determinar o filho MDI ativo</span><span class="sxs-lookup"><span data-stu-id="6d4ba-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="6d4ba-114">Fornece instruções de como verificar a janela filho que tem o foco (e enviar seu conteúdo para a área de transferência).</span><span class="sxs-lookup"><span data-stu-id="6d4ba-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="6d4ba-115">Como: Enviar dados para o filho MDI ativo</span><span class="sxs-lookup"><span data-stu-id="6d4ba-115">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="6d4ba-116">Fornece instruções de como transportar informações para a janela filho ativa.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="6d4ba-117">Como: Organizar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="6d4ba-117">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="6d4ba-118">Fornece instruções de como organizar lado a lado, em cascata ou organizar as janelas filho de um aplicativo MDI.</span><span class="sxs-lookup"><span data-stu-id="6d4ba-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
