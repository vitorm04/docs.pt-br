---
title: "Recuperando informações armazenadas em atributos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d3fd9a5a49d65b37d2cdb5107e9c516a6df5847
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="82f02-102">Recuperando informações armazenadas em atributos</span><span class="sxs-lookup"><span data-stu-id="82f02-102">Retrieving Information Stored in Attributes</span></span>
<span data-ttu-id="82f02-103">Recuperar um atributo personalizado é um processo simple.</span><span class="sxs-lookup"><span data-stu-id="82f02-103">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="82f02-104">Primeiro, declare uma instância do atributo que você deseja recuperar.</span><span class="sxs-lookup"><span data-stu-id="82f02-104">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="82f02-105">Em seguida, use o <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> método para inicializar o novo atributo para o valor do atributo que você deseja recuperar.</span><span class="sxs-lookup"><span data-stu-id="82f02-105">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="82f02-106">Depois que o novo atributo é inicializado, você simplesmente usar suas propriedades para obter os valores.</span><span class="sxs-lookup"><span data-stu-id="82f02-106">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="82f02-107">Este tópico descreve como recuperar os atributos de código carregados no contexto de execução.</span><span class="sxs-lookup"><span data-stu-id="82f02-107">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="82f02-108">Para recuperar os atributos de código carregados no contexto exclusivo de reflexão, você deve usar o <xref:System.Reflection.CustomAttributeData> classe, conforme mostrado no [como: carregar Assemblies no contexto de only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="82f02-108">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="82f02-109">Esta seção descreve as seguintes maneiras de recuperar os atributos:</span><span class="sxs-lookup"><span data-stu-id="82f02-109">This section describes the following ways to retrieve attributes:</span></span>  
  
-   [<span data-ttu-id="82f02-110">Recuperando uma única instância de um atributo</span><span class="sxs-lookup"><span data-stu-id="82f02-110">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
-   [<span data-ttu-id="82f02-111">Recuperando várias instâncias de um atributo aplicadas ao mesmo escopo</span><span class="sxs-lookup"><span data-stu-id="82f02-111">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [<span data-ttu-id="82f02-112">Recuperando várias instâncias de um atributo aplicadas a diferentes escopos</span><span class="sxs-lookup"><span data-stu-id="82f02-112">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="82f02-113">Recuperando uma única instância de um atributo</span><span class="sxs-lookup"><span data-stu-id="82f02-113">Retrieving a Single Instance of an Attribute</span></span>  
 <span data-ttu-id="82f02-114">No exemplo a seguir, o `DeveloperAttribute` (descrito na seção anterior) é aplicado para o `MainApp` classe no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="82f02-114">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="82f02-115">O `GetAttribute` método usa **GetCustomAttribute** para recuperar os valores armazenados em `DeveloperAttribute` no nível de classe antes de exibi-los no console.</span><span class="sxs-lookup"><span data-stu-id="82f02-115">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="82f02-116">Este programa exibe o texto a seguir quando executado.</span><span class="sxs-lookup"><span data-stu-id="82f02-116">This program displays the following text when executed.</span></span>  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="82f02-117">Se o atributo não for encontrado, o **GetCustomAttribute** método inicializa `MyAttribute` com um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="82f02-117">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="82f02-118">Este exemplo verifica `MyAttribute` para uma instância e notifica o usuário se nenhum atributo for encontrado.</span><span class="sxs-lookup"><span data-stu-id="82f02-118">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="82f02-119">Se o `DeveloperAttribute` não foi encontrado no escopo de classe, a seguinte mensagem será exibida no console.</span><span class="sxs-lookup"><span data-stu-id="82f02-119">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```  
The attribute was not found.   
```  
  
 <span data-ttu-id="82f02-120">Este exemplo supõe que a definição de atributo está no namespace atual.</span><span class="sxs-lookup"><span data-stu-id="82f02-120">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="82f02-121">Lembre-se de importar o namespace no qual a definição do atributo reside se ele não está no namespace atual.</span><span class="sxs-lookup"><span data-stu-id="82f02-121">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="82f02-122">Recuperando várias instâncias de um atributo aplicadas ao mesmo escopo</span><span class="sxs-lookup"><span data-stu-id="82f02-122">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  
 <span data-ttu-id="82f02-123">No exemplo anterior, a classe para inspecionar e o atributo específico para localizar são passados para <xref:System.Attribute.GetCustomAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="82f02-123">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="82f02-124">Esse código funciona bem se apenas uma instância de um atributo é aplicada no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="82f02-124">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="82f02-125">No entanto, se várias instâncias de um atributo forem aplicadas no mesmo nível de classe, o **GetCustomAttribute** método não recupera todas as informações.</span><span class="sxs-lookup"><span data-stu-id="82f02-125">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="82f02-126">Em casos onde várias instâncias do mesmo atributo são aplicadas ao mesmo escopo, você pode usar <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> para colocar todas as instâncias de um atributo em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="82f02-126">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="82f02-127">Por exemplo, se duas instâncias do `DeveloperAttribute` são aplicadas no nível de classe da mesma classe, o `GetAttribute` método pode ser modificado para exibir as informações encontradas em ambos os atributos.</span><span class="sxs-lookup"><span data-stu-id="82f02-127">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="82f02-128">Lembre-se de que, para aplicar vários atributos no mesmo nível, o atributo deve ser definido com o **AllowMultiple** propriedade definida como **true** no <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="82f02-128">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="82f02-129">O exemplo de código a seguir mostra como usar o **GetCustomAttributes** método para criar uma matriz que faz referência a todas as instâncias de `DeveloperAttribute` em qualquer determinada classe.</span><span class="sxs-lookup"><span data-stu-id="82f02-129">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="82f02-130">Os valores de todos os atributos são exibidos no console.</span><span class="sxs-lookup"><span data-stu-id="82f02-130">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="82f02-131">Se nenhum atributo for localizado, esse código alerta o usuário.</span><span class="sxs-lookup"><span data-stu-id="82f02-131">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="82f02-132">Caso contrário, as informações contidas em ambas as instâncias de `DeveloperAttribute` é exibido.</span><span class="sxs-lookup"><span data-stu-id="82f02-132">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="82f02-133">Recuperando várias instâncias de um atributo aplicadas a diferentes escopos</span><span class="sxs-lookup"><span data-stu-id="82f02-133">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  
 <span data-ttu-id="82f02-134">O <xref:System.Attribute.GetCustomAttributes%2A> e <xref:System.Attribute.GetCustomAttribute%2A> métodos não pesquisam uma classe inteira e retornam todas as instâncias de um atributo na classe.</span><span class="sxs-lookup"><span data-stu-id="82f02-134">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="82f02-135">Em vez disso, eles pesquisam somente um método especificado ou membro por vez.</span><span class="sxs-lookup"><span data-stu-id="82f02-135">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="82f02-136">Se você tiver uma classe com o mesmo atributo aplicado a cada membro e você deseja recuperar os valores em todos os atributos aplicados a esses membros, você deve fornecer cada método ou membro individualmente para **GetCustomAttributes** e  **GetCustomAttribute**.</span><span class="sxs-lookup"><span data-stu-id="82f02-136">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="82f02-137">O exemplo de código a seguir usa uma classe como um parâmetro e procura o `DeveloperAttribute` (definida anteriormente) no nível de classe e em cada método individual de classe.</span><span class="sxs-lookup"><span data-stu-id="82f02-137">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="82f02-138">Se nenhuma instância do `DeveloperAttribute` são encontradas no nível de método ou nível de classe, o `GetAttribute` método notifica o usuário que nenhum atributo foi encontrado e exibe o nome do método ou classe que contém o atributo.</span><span class="sxs-lookup"><span data-stu-id="82f02-138">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="82f02-139">Se um atributo for encontrado, o `Name`, `Level`, e `Reviewed` campos são exibidos no console.</span><span class="sxs-lookup"><span data-stu-id="82f02-139">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="82f02-140">Você pode usar os membros de <xref:System.Type> classe para obter os métodos e membros individuais na classe passada.</span><span class="sxs-lookup"><span data-stu-id="82f02-140">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="82f02-141">Este exemplo primeiro consulta o **tipo** objeto para obter informações de atributo para o nível de classe.</span><span class="sxs-lookup"><span data-stu-id="82f02-141">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="82f02-142">Em seguida, ele usa <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> para colocar instâncias de todos os métodos em uma matriz de <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objetos para recuperar informações de atributo para o nível de método.</span><span class="sxs-lookup"><span data-stu-id="82f02-142">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="82f02-143">Você também pode usar o <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> método para verificar os atributos no nível de propriedade ou <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> para verificar os atributos no nível do construtor.</span><span class="sxs-lookup"><span data-stu-id="82f02-143">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f02-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82f02-144">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="82f02-145">Atributos</span><span class="sxs-lookup"><span data-stu-id="82f02-145">Attributes</span></span>](../../../docs/standard/attributes/index.md)
