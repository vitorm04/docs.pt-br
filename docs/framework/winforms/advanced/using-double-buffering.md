---
title: Usando buffers duplos
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: 9b09210eba0ac3a141219a7cdbff15f22c6ed003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523904"
---
# <a name="using-double-buffering"></a><span data-ttu-id="85c44-102">Usando buffers duplos</span><span class="sxs-lookup"><span data-stu-id="85c44-102">Using Double Buffering</span></span>
<span data-ttu-id="85c44-103">Você pode usar elementos gráficos em buffer duplo para reduzir a cintilação em seus aplicativos que contêm operações complexas de pintura.</span><span class="sxs-lookup"><span data-stu-id="85c44-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="85c44-104">O .NET Framework contém suporte interno para o buffer duplo ou você pode gerenciar e processar imagens manualmente.</span><span class="sxs-lookup"><span data-stu-id="85c44-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85c44-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="85c44-105">In This Section</span></span>  
 [<span data-ttu-id="85c44-106">Elementos Gráficos em Buffer Duplo</span><span class="sxs-lookup"><span data-stu-id="85c44-106">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 <span data-ttu-id="85c44-107">Apresenta duplo buffer conceito e contornos do suporte do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="85c44-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="85c44-108">Como Reduzir a Cintilação em Elementos Gráficos com Buffers Duplos em Formulários e Controles</span><span class="sxs-lookup"><span data-stu-id="85c44-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="85c44-109">Demonstra como usar o padrão duplas buffer suporte no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="85c44-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="85c44-110">Como Gerenciar Elementos Gráficos em Buffer Manualmente</span><span class="sxs-lookup"><span data-stu-id="85c44-110">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="85c44-111">Mostra como gerenciar o buffer duplo em aplicativos.</span><span class="sxs-lookup"><span data-stu-id="85c44-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="85c44-112">Como Renderizar Elementos Gráficos em Buffer Manualmente</span><span class="sxs-lookup"><span data-stu-id="85c44-112">How to: Manually Render Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="85c44-113">Demonstra como renderizar elementos gráficos em buffer duplo.</span><span class="sxs-lookup"><span data-stu-id="85c44-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="85c44-114">Referência</span><span class="sxs-lookup"><span data-stu-id="85c44-114">Reference</span></span>  
 <span data-ttu-id="85c44-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span><span class="sxs-lookup"><span data-stu-id="85c44-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span></span>  
 <span data-ttu-id="85c44-116">Método de controle que permite que o buffer duplo.</span><span class="sxs-lookup"><span data-stu-id="85c44-116">Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="85c44-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span><span class="sxs-lookup"><span data-stu-id="85c44-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span></span>  
 <span data-ttu-id="85c44-118">Fornece métodos para a criação de buffers de gráficos.</span><span class="sxs-lookup"><span data-stu-id="85c44-118">Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="85c44-119">Fornece acesso ao contexto de elementos gráficos em buffer para um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85c44-119">Provides access to the buffered graphics context for a application domain.</span></span>
