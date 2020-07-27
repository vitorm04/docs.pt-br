---
title: Como implementar uma propriedade de dependência
description: Defina uma propriedade de dependência em Windows Presentation Foundation, fazendo backup de uma propriedade Common Language Runtime com um campo DependencyProperty.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: 673f653a9b02627efcccdfe08c4812ca0834217c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165094"
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="fd79a-103">Como implementar uma propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="fd79a-103">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="fd79a-104">Este exemplo mostra como fazer uma propriedade de Common Language Runtime (CLR) com um <xref:System.Windows.DependencyProperty> campo, definindo, portanto, uma propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="fd79a-104">This example shows how to back a common language runtime (CLR) property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="fd79a-105">Ao definir suas próprias propriedades, se deseja dar suporte a muitos aspectos de funcionalidades do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], incluindo estilos, vinculação de dados, herança, animação e valores padrão, você deve implementá-las como uma propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="fd79a-105">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd79a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fd79a-106">Example</span></span>  
 <span data-ttu-id="fd79a-107">O exemplo a seguir registra primeiro uma propriedade de dependência chamando o <xref:System.Windows.DependencyProperty.Register%2A> método.</span><span class="sxs-lookup"><span data-stu-id="fd79a-107">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="fd79a-108">O nome do campo de identificador que você usa para armazenar o nome e as características da propriedade de dependência deve ser o <xref:System.Windows.DependencyProperty.Name%2A> que você escolheu para a propriedade de dependência como parte da <xref:System.Windows.DependencyProperty.Register%2A> chamada, acrescentada pela cadeia de caracteres literal `Property` .</span><span class="sxs-lookup"><span data-stu-id="fd79a-108">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="fd79a-109">Por exemplo, se você registrar uma propriedade de dependência com um <xref:System.Windows.DependencyProperty.Name%2A> de `Location` , o campo identificador que você definir para a propriedade de dependência deverá ser `LocationProperty` nomeado.</span><span class="sxs-lookup"><span data-stu-id="fd79a-109">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="fd79a-110">Neste exemplo, o nome da propriedade de dependência e seu acessador CLR é `State` ; o campo identificador é `StateProperty` ; o tipo da propriedade é <xref:System.Boolean> ; e o tipo que registra a propriedade de dependência é `MyStateControl` .</span><span class="sxs-lookup"><span data-stu-id="fd79a-110">In this example, the name of the dependency property and its CLR accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="fd79a-111">Se você não conseguir seguir esse padrão de nomenclatura, os designers poderão não relatar sua propriedade corretamente e determinados aspectos do aplicativo de estilo do sistema de propriedade poderão não se comportar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="fd79a-111">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="fd79a-112">Também é possível especificar metadados padrão para uma propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="fd79a-112">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="fd79a-113">Esse exemplo registra o valor padrão da propriedade de dependência `State` como `false`.</span><span class="sxs-lookup"><span data-stu-id="fd79a-113">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="fd79a-114">Para obter mais informações sobre como e por que implementar uma propriedade de dependência, em vez de apenas fazer backup de uma propriedade CLR com um campo privado, consulte [visão geral das propriedades de dependência](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fd79a-114">For more information about how and why to implement a dependency property, as opposed to just backing a CLR property with a private field, see [Dependency Properties Overview](dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd79a-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="fd79a-115">See also</span></span>

- [<span data-ttu-id="fd79a-116">Visão geral das propriedades de dependência</span><span class="sxs-lookup"><span data-stu-id="fd79a-116">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="fd79a-117">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="fd79a-117">How-to Topics</span></span>](properties-how-to-topics.md)
