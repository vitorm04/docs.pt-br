---
title: Usando buffers duplos
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: ac6c9b7f2cc1fea86a75eaaf4a2dde1ea60e4f40
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716264"
---
# <a name="using-double-buffering"></a><span data-ttu-id="a5965-102">Usando buffers duplos</span><span class="sxs-lookup"><span data-stu-id="a5965-102">Using Double Buffering</span></span>
<span data-ttu-id="a5965-103">Você pode usar gráficos em buffer duplo para reduzir a cintilação em seus aplicativos que contêm operações de pintura complexas.</span><span class="sxs-lookup"><span data-stu-id="a5965-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="a5965-104">O .NET Framework contém suporte interno para buffer duplo ou você pode gerenciar e renderizar elementos gráficos manualmente.</span><span class="sxs-lookup"><span data-stu-id="a5965-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a5965-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a5965-105">In This Section</span></span>  
 [<span data-ttu-id="a5965-106">Elementos Gráficos em Buffer Duplo</span><span class="sxs-lookup"><span data-stu-id="a5965-106">Double Buffered Graphics</span></span>](double-buffered-graphics.md)  
 <span data-ttu-id="a5965-107">Apresenta duplas buffer conceito e contornos de suporte do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a5965-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="a5965-108">Como: Reduzir a cintilação em elementos gráficos com buffers duplos para formulários e controles</span><span class="sxs-lookup"><span data-stu-id="a5965-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="a5965-109">Demonstra como usar o padrão buffer suporte no .NET Framework duplo.</span><span class="sxs-lookup"><span data-stu-id="a5965-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="a5965-110">Como: Gerenciar elementos gráficos em buffer manualmente</span><span class="sxs-lookup"><span data-stu-id="a5965-110">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="a5965-111">Mostra como gerenciar o buffer duplo em aplicativos.</span><span class="sxs-lookup"><span data-stu-id="a5965-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="a5965-112">Como: Renderizar elementos gráficos em buffer manualmente</span><span class="sxs-lookup"><span data-stu-id="a5965-112">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="a5965-113">Demonstra como renderizar elementos gráficos em buffer duplo.</span><span class="sxs-lookup"><span data-stu-id="a5965-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a5965-114">Referência</span><span class="sxs-lookup"><span data-stu-id="a5965-114">Reference</span></span>  
 <span data-ttu-id="a5965-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span><span class="sxs-lookup"><span data-stu-id="a5965-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span></span>  
 <span data-ttu-id="a5965-116">Método de controle que permite que o buffer duplo.</span><span class="sxs-lookup"><span data-stu-id="a5965-116">Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="a5965-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span><span class="sxs-lookup"><span data-stu-id="a5965-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span></span>  
 <span data-ttu-id="a5965-118">Fornece métodos para criação de buffers gráficos.</span><span class="sxs-lookup"><span data-stu-id="a5965-118">Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="a5965-119">Fornece acesso ao contexto de elementos gráficos em buffer para um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5965-119">Provides access to the buffered graphics context for a application domain.</span></span>
