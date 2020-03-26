---
title: 'Como: Criar uma cena 3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3D
- 3D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: 36453894e06e7b59f339c21713449140c17f6851
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112096"
---
# <a name="how-to-create-a-3d-scene"></a><span data-ttu-id="657a3-102">Como: Criar uma cena 3D</span><span class="sxs-lookup"><span data-stu-id="657a3-102">How to: Create a 3D Scene</span></span>
<span data-ttu-id="657a3-103">Este exemplo mostra como criar um objeto 3D que se parece com uma folha plana de papel que foi girada.</span><span class="sxs-lookup"><span data-stu-id="657a3-103">This example shows how to create a 3D object that looks like a flat sheet of paper which has been rotated.</span></span> <span data-ttu-id="657a3-104">Juntamente <xref:System.Windows.Controls.Viewport3D> com os seguintes componentes são usados para criar esta simples cena 3D:</span><span class="sxs-lookup"><span data-stu-id="657a3-104">A <xref:System.Windows.Controls.Viewport3D> along with the following components are used to create this simple 3D scene:</span></span>  
  
- <span data-ttu-id="657a3-105">Uma câmera é criada <xref:System.Windows.Media.Media3D.PerspectiveCamera>usando um .</span><span class="sxs-lookup"><span data-stu-id="657a3-105">A camera is created using a <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="657a3-106">A câmera especifica qual parte da cena 3D é visível.</span><span class="sxs-lookup"><span data-stu-id="657a3-106">The camera specifies what part of the 3D scene is viewable.</span></span>  
  
- <span data-ttu-id="657a3-107">Uma malha é criada para especificar a forma do objeto <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> 3D (folha de papel) usando a propriedade de <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="657a3-107">A mesh is created to specify the shape of 3D object (sheet of paper) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
- <span data-ttu-id="657a3-108">Um material é especificado para ser exibido na superfície do objeto (gradiente linear nesta amostra) usando a <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> propriedade de <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="657a3-108">A material is specified to be displayed on the surface of the object (linear gradient in this sample) using the <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
- <span data-ttu-id="657a3-109">Uma luz é criada para brilhar <xref:System.Windows.Media.Media3D.DirectionalLight>sobre o objeto usando .</span><span class="sxs-lookup"><span data-stu-id="657a3-109">A light is created to shine on the object using <xref:System.Windows.Media.Media3D.DirectionalLight>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="657a3-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="657a3-110">Example</span></span>  
 <span data-ttu-id="657a3-111">O código abaixo mostra como criar uma cena 3D em XAML.</span><span class="sxs-lookup"><span data-stu-id="657a3-111">The code below shows how to create a 3D scene in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="657a3-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="657a3-112">Example</span></span>  
 <span data-ttu-id="657a3-113">O código abaixo mostra como criar a mesma cena 3D no código processual.</span><span class="sxs-lookup"><span data-stu-id="657a3-113">The code below shows how to create the same 3D scene in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="657a3-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="657a3-114">See also</span></span>

- [<span data-ttu-id="657a3-115">Visão geral de gráficos 3D</span><span class="sxs-lookup"><span data-stu-id="657a3-115">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
