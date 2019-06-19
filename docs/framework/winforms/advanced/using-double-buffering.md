---
title: Usando buffers duplos
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: 5b22336221c7bdda3c9dd7adf23308a2b0bad450
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169914"
---
# <a name="using-double-buffering"></a><span data-ttu-id="8c391-102">Usando buffers duplos</span><span class="sxs-lookup"><span data-stu-id="8c391-102">Using Double Buffering</span></span>
<span data-ttu-id="8c391-103">Você pode usar gráficos em buffer duplo para reduzir a cintilação em seus aplicativos que contêm operações de pintura complexas.</span><span class="sxs-lookup"><span data-stu-id="8c391-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="8c391-104">O .NET Framework contém suporte interno para buffer duplo ou você pode gerenciar e renderizar elementos gráficos manualmente.</span><span class="sxs-lookup"><span data-stu-id="8c391-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c391-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8c391-105">In This Section</span></span>  
 [<span data-ttu-id="8c391-106">Elementos Gráficos em Buffer Duplo</span><span class="sxs-lookup"><span data-stu-id="8c391-106">Double Buffered Graphics</span></span>](double-buffered-graphics.md)  
 <span data-ttu-id="8c391-107">Apresenta duplas buffer conceito e contornos de suporte do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c391-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="8c391-108">Como: Reduzir a cintilação em elementos gráficos com buffers duplos para formulários e controles</span><span class="sxs-lookup"><span data-stu-id="8c391-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="8c391-109">Demonstra como usar o padrão buffer suporte no .NET Framework duplo.</span><span class="sxs-lookup"><span data-stu-id="8c391-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="8c391-110">Como: Gerenciar elementos gráficos em buffer manualmente</span><span class="sxs-lookup"><span data-stu-id="8c391-110">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="8c391-111">Mostra como gerenciar o buffer duplo em aplicativos.</span><span class="sxs-lookup"><span data-stu-id="8c391-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="8c391-112">Como: Renderizar elementos gráficos em buffer manualmente</span><span class="sxs-lookup"><span data-stu-id="8c391-112">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="8c391-113">Demonstra como renderizar elementos gráficos em buffer duplo.</span><span class="sxs-lookup"><span data-stu-id="8c391-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8c391-114">Referência</span><span class="sxs-lookup"><span data-stu-id="8c391-114">Reference</span></span>  
 <span data-ttu-id="8c391-115"><xref:System.Windows.Forms.Control.SetStyle%2A> Método de controle que permite que o buffer duplo.</span><span class="sxs-lookup"><span data-stu-id="8c391-115"><xref:System.Windows.Forms.Control.SetStyle%2A> Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="8c391-116"><xref:System.Drawing.BufferedGraphicsContext> Fornece métodos para criação de buffers gráficos.</span><span class="sxs-lookup"><span data-stu-id="8c391-116"><xref:System.Drawing.BufferedGraphicsContext> Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="8c391-117">Fornece acesso ao contexto de elementos gráficos em buffer para um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8c391-117">Provides access to the buffered graphics context for a application domain.</span></span>
