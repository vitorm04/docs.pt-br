---
title: Acessando atributos personalizados
description: Acesse atributos personalizados no .NET. Depois que os atributos tiverem sido associados aos elementos do programa, você poderá usar a reflexão para consultar sua existência e valores.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
ms.openlocfilehash: 1197fc5149e144d293deda1173e82ca2dadeda7d
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475132"
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="02eb0-104">Acessando atributos personalizados</span><span class="sxs-lookup"><span data-stu-id="02eb0-104">Accessing Custom Attributes</span></span>
<span data-ttu-id="02eb0-105">Depois que os atributos tiverem sido associados aos elementos do programa, a reflexão poderá ser usada para consultar sua existência e seus valores.</span><span class="sxs-lookup"><span data-stu-id="02eb0-105">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="02eb0-106">No .NET Framework versão 1.0 e 1.1, os atributos personalizados são examinados no contexto de execução.</span><span class="sxs-lookup"><span data-stu-id="02eb0-106">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="02eb0-107">O .NET Framework versão 2.0 fornece um novo contexto de carregamento, o contexto somente para reflexão, que pode ser usado para examinar o código que não pode ser carregado para execução.</span><span class="sxs-lookup"><span data-stu-id="02eb0-107">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="02eb0-108">O contexto somente para reflexão</span><span class="sxs-lookup"><span data-stu-id="02eb0-108">The Reflection-Only Context</span></span>  
 <span data-ttu-id="02eb0-109">O código carregado no contexto somente para reflexão não pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="02eb0-109">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="02eb0-110">Isso significa que instâncias de atributos personalizados não podem ser criadas porque isso exigiria a execução de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="02eb0-110">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="02eb0-111">Para carregar e examinar os atributos personalizados no contexto somente para reflexão, use a classe <xref:System.Reflection.CustomAttributeData>.</span><span class="sxs-lookup"><span data-stu-id="02eb0-111">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="02eb0-112">Você pode obter as instâncias dessa classe usando a sobrecarga apropriada do método <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> estático.</span><span class="sxs-lookup"><span data-stu-id="02eb0-112">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="02eb0-113">Consulte [Como carregar assemblies no contexto de somente para reflexão](how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="02eb0-113">See [How to: Load Assemblies into the Reflection-Only Context](how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="02eb0-114">O contexto de execução</span><span class="sxs-lookup"><span data-stu-id="02eb0-114">The Execution Context</span></span>  
 <span data-ttu-id="02eb0-115">Os principais métodos de reflexão para consultar atributos no contexto de execução são <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> e <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02eb0-115">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="02eb0-116">A acessibilidade de um atributo personalizado é verificada em relação ao assembly no qual ele está anexado.</span><span class="sxs-lookup"><span data-stu-id="02eb0-116">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="02eb0-117">Isso é equivalente a verificar se um método em um tipo no assembly no qual o atributo personalizado está anexado pode chamar o construtor do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="02eb0-117">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="02eb0-118">Métodos como <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> verificam a visibilidade e a acessibilidade do argumento de tipo.</span><span class="sxs-lookup"><span data-stu-id="02eb0-118">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="02eb0-119">Somente o código no assembly que contém o tipo definido pelo usuário pode recuperar um atributo personalizado desse tipo usando **GetCustomAttributes**.</span><span class="sxs-lookup"><span data-stu-id="02eb0-119">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="02eb0-120">O exemplo de C# a seguir é um padrão de design de atributo personalizado típico.</span><span class="sxs-lookup"><span data-stu-id="02eb0-120">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="02eb0-121">Ele ilustra o modelo de reflexão do atributo personalizado em runtime.</span><span class="sxs-lookup"><span data-stu-id="02eb0-121">It illustrates the runtime custom attribute reflection model.</span></span>  
  
```csharp
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 <span data-ttu-id="02eb0-122">Se o runtime estiver tentando recuperar os atributos personalizados para o tipo de atributo personalizado público <xref:System.ComponentModel.DescriptionAttribute> anexado ao método **GetLanguage**, ele executará as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="02eb0-122">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1. <span data-ttu-id="02eb0-123">O runtime verifica se o argumento de tipo **DescriptionAttribute** para **Type.GetCustomAttributes**(Tipo *type*) é público e, portanto, está visível e acessível.</span><span class="sxs-lookup"><span data-stu-id="02eb0-123">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2. <span data-ttu-id="02eb0-124">O runtime verifica se o tipo definido pelo usuário **MyDescriptionAttribute** que é derivado de **DescriptionAttribute** está visível e acessível dentro do assembly **System.Web.DLL**, onde ele está anexado ao método **GetLanguage**().</span><span class="sxs-lookup"><span data-stu-id="02eb0-124">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3. <span data-ttu-id="02eb0-125">O runtime verifica se o construtor de **MyDescriptionAttribute** está visível e acessível dentro do assembly **System.Web.DLL**.</span><span class="sxs-lookup"><span data-stu-id="02eb0-125">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4. <span data-ttu-id="02eb0-126">O runtime chama o construtor de **MyDescriptionAttribute** com os parâmetros do atributo personalizado e retorna o novo objeto ao chamador.</span><span class="sxs-lookup"><span data-stu-id="02eb0-126">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="02eb0-127">O modelo de reflexão do atributo personalizado pode causar perda de instâncias de tipos definidos pelo usuário fora do assembly no qual o tipo é definido.</span><span class="sxs-lookup"><span data-stu-id="02eb0-127">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="02eb0-128">Isso não é diferente dos membros na biblioteca do sistema do tempo de execução que retornam instâncias de tipos definidos pelo usuário, como <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> que retorna uma matriz de objetos **RuntimeMethodInfo**.</span><span class="sxs-lookup"><span data-stu-id="02eb0-128">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="02eb0-129">Para impedir que um cliente descubra informações sobre um tipo de atributo personalizado definido pelo usuário, defina os membros do tipo como confidenciais.</span><span class="sxs-lookup"><span data-stu-id="02eb0-129">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="02eb0-130">O exemplo a seguir demonstra a maneira básica de usar a reflexão para obter acesso a atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="02eb0-130">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="02eb0-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02eb0-131">See also</span></span>

- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="02eb0-132">Exibindo informações de tipo</span><span class="sxs-lookup"><span data-stu-id="02eb0-132">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="02eb0-133">Considerações sobre segurança relacionadas à reflexão</span><span class="sxs-lookup"><span data-stu-id="02eb0-133">Security Considerations for Reflection</span></span>](security-considerations-for-reflection.md)
