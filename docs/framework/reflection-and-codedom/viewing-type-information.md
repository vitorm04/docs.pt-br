---
title: Exibindo informações de tipo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- types, viewing type information
- Type object
- viewing type information
- reflection, viewing type information
ms.assetid: 7e7303a9-4064-4738-b4e7-b75974ed70d2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5417f330040c2b6ce08a53920f9a92117624a80
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045766"
---
# <a name="viewing-type-information"></a><span data-ttu-id="5fe09-102">Exibindo informações de tipo</span><span class="sxs-lookup"><span data-stu-id="5fe09-102">Viewing Type Information</span></span>
<span data-ttu-id="5fe09-103">A classe <xref:System.Type?displayProperty=nameWithType> é fundamental para reflexão.</span><span class="sxs-lookup"><span data-stu-id="5fe09-103">The <xref:System.Type?displayProperty=nameWithType> class is central to reflection.</span></span> <span data-ttu-id="5fe09-104">O Common Language Runtime cria o **Type** para um tipo carregado quando a reflexão solicitá-lo.</span><span class="sxs-lookup"><span data-stu-id="5fe09-104">The common language runtime creates the **Type** for a loaded type when reflection requests it.</span></span> <span data-ttu-id="5fe09-105">Você pode usar os métodos, campos, propriedades e classes aninhadas de um objeto **Tipo** para descobrir tudo sobre o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="5fe09-105">You can use a **Type** object's methods, fields, properties, and nested classes to find out everything about that type.</span></span>  
  
 <span data-ttu-id="5fe09-106">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> para obter objetos **Tipo** de assemblies que não foram carregados, passando o nome do tipo ou tipos que você deseja.</span><span class="sxs-lookup"><span data-stu-id="5fe09-106">Use <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> to obtain **Type** objects from assemblies that have not been loaded, passing in the name of the type or types you want.</span></span> <span data-ttu-id="5fe09-107">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> para obter objetos **Tipo** de um assembly que já foi carregado.</span><span class="sxs-lookup"><span data-stu-id="5fe09-107">Use <xref:System.Type.GetType%2A?displayProperty=nameWithType> to get the **Type** objects from an assembly that is already loaded.</span></span> <span data-ttu-id="5fe09-108">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> e <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> para obter objetos **Type** do módulo.</span><span class="sxs-lookup"><span data-stu-id="5fe09-108">Use <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> and <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType> to obtain module **Type** objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5fe09-109">Caso deseje examinar e manipular métodos e tipos genéricos, confira as informações adicionais fornecidas em [Reflexão e tipos genéricos](reflection-and-generic-types.md) e [Como: Examinar tipos genéricos e criar instâncias deles com a reflexão](how-to-examine-and-instantiate-generic-types-with-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="5fe09-109">If you want to examine and manipulate generic types and methods, please see the additional information provided in [Reflection and Generic Types](reflection-and-generic-types.md) and [How to: Examine and Instantiate Generic Types with Reflection](how-to-examine-and-instantiate-generic-types-with-reflection.md).</span></span>  
  
 <span data-ttu-id="5fe09-110">O exemplo a seguir mostra a sintaxe necessária obter o objeto <xref:System.Reflection.Assembly> e o módulo para um assembly.</span><span class="sxs-lookup"><span data-stu-id="5fe09-110">The following example shows the syntax necessary to get the <xref:System.Reflection.Assembly> object and module for an assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#6)]
 [!code-csharp[Conceptual.Types.ViewInfo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#6)]
 [!code-vb[Conceptual.Types.ViewInfo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#6)]  
  
 <span data-ttu-id="5fe09-111">O exemplo a seguir demonstra como obter objetos de **Tipo** de um assembly carregado.</span><span class="sxs-lookup"><span data-stu-id="5fe09-111">The following example demonstrates getting **Type** objects from a loaded assembly.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source5.cpp#7)]
 [!code-csharp[Conceptual.Types.ViewInfo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source5.cs#7)]
 [!code-vb[Conceptual.Types.ViewInfo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source5.vb#7)]  
  
 <span data-ttu-id="5fe09-112">Depois de obter um **Tipo**, há várias maneiras de descobrir informações sobre os membros desse tipo.</span><span class="sxs-lookup"><span data-stu-id="5fe09-112">Once you obtain a **Type**, there are many ways you can discover information about the members of that type.</span></span> <span data-ttu-id="5fe09-113">Por exemplo, você pode descobrir sobre todos os membros do tipo chamando o método <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>, que obtém uma matriz de objetos <xref:System.Reflection.MemberInfo> que descrevem cada um dos membros do tipo atual.</span><span class="sxs-lookup"><span data-stu-id="5fe09-113">For example, you can find out about all the type's members by calling the <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> method, which obtains an array of <xref:System.Reflection.MemberInfo> objects describing each of the members of the current type.</span></span>  
  
 <span data-ttu-id="5fe09-114">Você também pode usar métodos na classe **Tipo** para recuperar informações sobre um ou mais construtores, métodos, eventos, campos ou propriedades que você especifica por nome.</span><span class="sxs-lookup"><span data-stu-id="5fe09-114">You can also use methods on the **Type** class to retrieve information about one or more constructors, methods, events, fields, or properties that you specify by name.</span></span> <span data-ttu-id="5fe09-115">Por exemplo, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsula um construtor específico da classe atual.</span><span class="sxs-lookup"><span data-stu-id="5fe09-115">For example, <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType> encapsulates a specific constructor of the current class.</span></span>  
  
 <span data-ttu-id="5fe09-116">Se você tiver um **Tipo**, poderá usar a propriedade <xref:System.Type.Module%2A?displayProperty=nameWithType> para obter um objeto que encapsula o módulo que contém esse tipo.</span><span class="sxs-lookup"><span data-stu-id="5fe09-116">If you have a **Type**, you can use the <xref:System.Type.Module%2A?displayProperty=nameWithType> property to obtain an object that encapsulates the module containing that type.</span></span> <span data-ttu-id="5fe09-117">Use a propriedade <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> para localizar um objeto que encapsula o assembly que contém o módulo.</span><span class="sxs-lookup"><span data-stu-id="5fe09-117">Use the <xref:System.Reflection.Module.Assembly%2A?displayProperty=nameWithType> property to locate an object that encapsulates the assembly containing the module.</span></span> <span data-ttu-id="5fe09-118">Você pode obter o assembly que encapsula o tipo diretamente usando a propriedade <xref:System.Type.Assembly%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5fe09-118">You can obtain the assembly that encapsulates the type directly by using the <xref:System.Type.Assembly%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="systemtype-and-constructorinfo"></a><span data-ttu-id="5fe09-119">System.Type e ConstructorInfo</span><span class="sxs-lookup"><span data-stu-id="5fe09-119">System.Type and ConstructorInfo</span></span>  
 <span data-ttu-id="5fe09-120">O exemplo a seguir mostra como listar os construtores de uma classe, nesse caso, a classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5fe09-120">The following example shows how to list the constructors for a class, in this case, the <xref:System.String> class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.ViewInfo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.ViewInfo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source1.vb#1)]  
  
## <a name="memberinfo-methodinfo-fieldinfo-and-propertyinfo"></a><span data-ttu-id="5fe09-121">MemberInfo, MethodInfo, FieldInfo e PropertyInfo</span><span class="sxs-lookup"><span data-stu-id="5fe09-121">MemberInfo, MethodInfo, FieldInfo, and PropertyInfo</span></span>  
 <span data-ttu-id="5fe09-122">Obtenha informações sobre métodos, propriedades, eventos e campos do tipo usando os objetos <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo> ou <xref:System.Reflection.PropertyInfo>.</span><span class="sxs-lookup"><span data-stu-id="5fe09-122">Obtain information about the type's methods, properties, events, and fields using <xref:System.Reflection.MemberInfo>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.FieldInfo>, or <xref:System.Reflection.PropertyInfo> objects.</span></span>  
  
 <span data-ttu-id="5fe09-123">O exemplo a seguir usa **MemberInfo** para listar o número de membros na classe **System.IO.File** e usa a propriedade <xref:System.Type.IsPublic%2A> para determinar a visibilidade da classe.</span><span class="sxs-lookup"><span data-stu-id="5fe09-123">The following example uses **MemberInfo** to list the number of members in the **System.IO.File** class and uses the <xref:System.Type.IsPublic%2A> property to determine the visibility of the class.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.ViewInfo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.ViewInfo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source2.vb#2)]  
  
 <span data-ttu-id="5fe09-124">O exemplo a seguir examina o tipo do membro especificado.</span><span class="sxs-lookup"><span data-stu-id="5fe09-124">The following example investigates the type of the specified member.</span></span> <span data-ttu-id="5fe09-125">Ele executa reflexão em um membro da classe **MemberInfo** e lista seu tipo.</span><span class="sxs-lookup"><span data-stu-id="5fe09-125">It performs reflection on a member of the **MemberInfo** class, and lists its type.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.Types.ViewInfo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source3.cs#3)]
 [!code-vb[Conceptual.Types.ViewInfo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source3.vb#3)]  
  
 <span data-ttu-id="5fe09-126">O exemplo a seguir usa todas as classes Reflection **\*Info** junto com <xref:System.Reflection.BindingFlags> para listar todos os membros (construtores, campos, propriedades, eventos e métodos) da classe especificada, dividindo os membros em categorias de instância e estáticos.</span><span class="sxs-lookup"><span data-stu-id="5fe09-126">The following example uses all the Reflection **\*Info** classes along with <xref:System.Reflection.BindingFlags> to list all the members (constructors, fields, properties, events, and methods) of the specified class, dividing the members into static and instance categories.</span></span>  
  
 [!code-cpp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.Types.ViewInfo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source4.cs#4)]
 [!code-vb[Conceptual.Types.ViewInfo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5fe09-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fe09-127">See also</span></span>

- <xref:System.Reflection.BindingFlags>
- <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>
- <xref:System.Type.GetFields%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Module.GetTypes%2A?displayProperty=nameWithType>
- <xref:System.Reflection.MemberInfo>
- <xref:System.Reflection.ConstructorInfo>
- <xref:System.Reflection.MethodInfo>
- <xref:System.Reflection.FieldInfo>
- <xref:System.Reflection.EventInfo>
- <xref:System.Reflection.ParameterInfo>
- [<span data-ttu-id="5fe09-128">Reflexão e tipos genéricos</span><span class="sxs-lookup"><span data-stu-id="5fe09-128">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)
