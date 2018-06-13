---
title: Usando contêineres de elementos gráficos
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
ms.openlocfilehash: 8755a95434d3fed06a55cfca0f71d86e5521cb39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525015"
---
# <a name="using-graphics-containers"></a><span data-ttu-id="8aa24-102">Usando contêineres de elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="8aa24-102">Using Graphics Containers</span></span>
<span data-ttu-id="8aa24-103">Um <xref:System.Drawing.Graphics> objeto fornece métodos como <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, e <xref:System.Drawing.Graphics.DrawString%2A> para exibir imagens de vetor, imagens de varredura e texto.</span><span class="sxs-lookup"><span data-stu-id="8aa24-103">A <xref:System.Drawing.Graphics> object provides methods such as <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, and <xref:System.Drawing.Graphics.DrawString%2A> for displaying vector images, raster images, and text.</span></span> <span data-ttu-id="8aa24-104">Um <xref:System.Drawing.Graphics> objeto também tem várias propriedades que influenciam a qualidade e a orientação dos itens que são desenhadas.</span><span class="sxs-lookup"><span data-stu-id="8aa24-104">A <xref:System.Drawing.Graphics> object also has several properties that influence the quality and orientation of the items that are drawn.</span></span> <span data-ttu-id="8aa24-105">Por exemplo, a propriedade de modo de suavização determina se a suavização é aplicada às linhas e curvas e a propriedade de transformação global influencia a posição e a rotação dos itens que são desenhados.</span><span class="sxs-lookup"><span data-stu-id="8aa24-105">For example, the smoothing mode property determines whether antialiasing is applied to lines and curves, and the world transformation property influences the position and rotation of the items that are drawn.</span></span>  
  
 <span data-ttu-id="8aa24-106">Um <xref:System.Drawing.Graphics> objeto está associado um dispositivo de vídeo específico.</span><span class="sxs-lookup"><span data-stu-id="8aa24-106">A <xref:System.Drawing.Graphics> object is associated with a particular display device.</span></span> <span data-ttu-id="8aa24-107">Quando você usa um <xref:System.Drawing.Graphics> objeto ao desenhar em uma janela, o <xref:System.Drawing.Graphics> objeto também é associado essa janela específica.</span><span class="sxs-lookup"><span data-stu-id="8aa24-107">When you use a <xref:System.Drawing.Graphics> object to draw in a window, the <xref:System.Drawing.Graphics> object is also associated with that particular window.</span></span>  
  
 <span data-ttu-id="8aa24-108">Um <xref:System.Drawing.Graphics> objeto pode ser pensado como um contêiner porque ele contém um conjunto de propriedades que influenciam o desenho e está vinculada a informações específicas de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8aa24-108">A <xref:System.Drawing.Graphics> object can be thought of as a container because it holds a set of properties that influence drawing and it is linked to device-specific information.</span></span> <span data-ttu-id="8aa24-109">Você pode criar um contêiner secundário dentro de uma existente <xref:System.Drawing.Graphics> objeto chamando o <xref:System.Drawing.Graphics.BeginContainer%2A> método que <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="8aa24-109">You can create a secondary container within an existing <xref:System.Drawing.Graphics> object by calling the <xref:System.Drawing.Graphics.BeginContainer%2A> method of that <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8aa24-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8aa24-110">In This Section</span></span>  
 [<span data-ttu-id="8aa24-111">Gerenciando o Estado de um Objeto Gráfico</span><span class="sxs-lookup"><span data-stu-id="8aa24-111">Managing the State of a Graphics Object</span></span>](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 <span data-ttu-id="8aa24-112">Descreve como gerenciar configurações de qualidade, a área de recorte e transformações de um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="8aa24-112">Describes how manage the quality settings, clipping area and transformations of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [<span data-ttu-id="8aa24-113">Usando Contêineres de Elementos Gráficos Aninhados</span><span class="sxs-lookup"><span data-stu-id="8aa24-113">Using Nested Graphics Containers</span></span>](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 <span data-ttu-id="8aa24-114">Mostra como usar contêineres para controlar o estado do <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="8aa24-114">Shows how to use containers to control the state of the <xref:System.Drawing.Graphics> object.</span></span>
