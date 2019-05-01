---
title: 'Como: Testar estruturas Point4D para igualdade e desigualdade'
ms.date: 03/30/2017
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
ms.openlocfilehash: ce1188e99ef2b0682427cc2e227aaccd27f7c4f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050630"
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a><span data-ttu-id="55333-102">Como: Testar estruturas Point4D para igualdade e desigualdade</span><span class="sxs-lookup"><span data-stu-id="55333-102">How to: Test Point4D structures for equality and inequality</span></span>
<span data-ttu-id="55333-103">Este exemplo mostra como testar <xref:System.Windows.Media.Media3D.Point4D> estruturas para igualdade e desigualdade.</span><span class="sxs-lookup"><span data-stu-id="55333-103">This example shows how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality.</span></span>  
  
 <span data-ttu-id="55333-104">O código a seguir ilustra como testar <xref:System.Windows.Media.Media3D.Point4D> estruturas para igualdade e desigualdade usando o <xref:System.Windows.Media.Media3D.Point4D> métodos de igualdade.</span><span class="sxs-lookup"><span data-stu-id="55333-104">The following code illustrates how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality using the <xref:System.Windows.Media.Media3D.Point4D> equality methods.</span></span>  <span data-ttu-id="55333-105">O <xref:System.Windows.Media.Media3D.Point4D> estruturas são testadas quanto à igualdade usando a igualdade sobrecarregada (`==`) operador, em seguida, para desigualdade usando o operador de desigualdade sobrecarregado (`!=`) operador e, finalmente, uma <xref:System.Windows.Media.Media3D.Point3D> estrutura e um <xref:System.Windows.Media.Media3D.Point4D> estrutura são verificados quanto à igualdade usando estático <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> método.</span><span class="sxs-lookup"><span data-stu-id="55333-105">The <xref:System.Windows.Media.Media3D.Point4D> structures are tested for equality using the overloaded equality (`==`) operator, then for inequality using the overloaded inequality (`!=`) operator, and finally a <xref:System.Windows.Media.Media3D.Point3D> structure and a <xref:System.Windows.Media.Media3D.Point4D> structure are checked for equality using the static <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55333-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55333-106">Example</span></span>  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a><span data-ttu-id="55333-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55333-107">See also</span></span>

- <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
