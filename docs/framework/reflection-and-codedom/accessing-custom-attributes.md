---
title: Acessando atributos personalizados
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aafd1586068dcd7aaf4a72ef5454e3a2698ccd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397085"
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="2899b-102">Acessando atributos personalizados</span><span class="sxs-lookup"><span data-stu-id="2899b-102">Accessing Custom Attributes</span></span>
<span data-ttu-id="2899b-103">Depois que os atributos tiverem sido associados aos elementos do programa, a reflexão poderá ser usada para consultar sua existência e seus valores.</span><span class="sxs-lookup"><span data-stu-id="2899b-103">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="2899b-104">No .NET Framework versão 1.0 e 1.1, os atributos personalizados são examinados no contexto de execução.</span><span class="sxs-lookup"><span data-stu-id="2899b-104">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="2899b-105">O .NET Framework versão 2.0 fornece um novo contexto de carregamento, o contexto somente para reflexão, que pode ser usado para examinar o código que não pode ser carregado para execução.</span><span class="sxs-lookup"><span data-stu-id="2899b-105">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="2899b-106">O contexto somente para reflexão</span><span class="sxs-lookup"><span data-stu-id="2899b-106">The Reflection-Only Context</span></span>  
 <span data-ttu-id="2899b-107">O código carregado no contexto somente para reflexão não pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="2899b-107">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="2899b-108">Isso significa que instâncias de atributos personalizados não podem ser criadas porque isso exigiria a execução de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="2899b-108">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="2899b-109">Para carregar e examinar os atributos personalizados no contexto somente para reflexão, use a classe <xref:System.Reflection.CustomAttributeData>.</span><span class="sxs-lookup"><span data-stu-id="2899b-109">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="2899b-110">Você pode obter as instâncias dessa classe usando a sobrecarga apropriada do método <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> estático.</span><span class="sxs-lookup"><span data-stu-id="2899b-110">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2899b-111">Consulte [Como carregar assemblies no contexto de somente para reflexão](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="2899b-111">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="2899b-112">O contexto de execução</span><span class="sxs-lookup"><span data-stu-id="2899b-112">The Execution Context</span></span>  
 <span data-ttu-id="2899b-113">Os principais métodos de reflexão para consultar atributos no contexto de execução são <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> e <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2899b-113">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="2899b-114">A acessibilidade de um atributo personalizado é verificada em relação ao assembly no qual ele está anexado.</span><span class="sxs-lookup"><span data-stu-id="2899b-114">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="2899b-115">Isso é equivalente a verificar se um método em um tipo no assembly no qual o atributo personalizado está anexado pode chamar o construtor do atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="2899b-115">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="2899b-116">Métodos como <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> verificam a visibilidade e a acessibilidade do argumento de tipo.</span><span class="sxs-lookup"><span data-stu-id="2899b-116">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="2899b-117">Somente o código no assembly que contém o tipo definido pelo usuário pode recuperar um atributo personalizado desse tipo usando **GetCustomAttributes**.</span><span class="sxs-lookup"><span data-stu-id="2899b-117">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="2899b-118">O exemplo de C# a seguir é um padrão de design de atributo personalizado típico.</span><span class="sxs-lookup"><span data-stu-id="2899b-118">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="2899b-119">Ele ilustra o modelo de reflexão do atributo personalizado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2899b-119">It illustrates the runtime custom attribute reflection model.</span></span>  
  
```  
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
  
 <span data-ttu-id="2899b-120">Se o tempo de execução estiver tentando recuperar os atributos personalizados para o tipo de atributo personalizado público <xref:System.ComponentModel.DescriptionAttribute> anexado ao método **GetLanguage**, ele executará as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="2899b-120">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1.  <span data-ttu-id="2899b-121">O tempo de execução verifica se o argumento de tipo **DescriptionAttribute** para **Type.GetCustomAttributes**(Tipo *type*) é público e, portanto, está visível e acessível.</span><span class="sxs-lookup"><span data-stu-id="2899b-121">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2.  <span data-ttu-id="2899b-122">O tempo de execução verifica se o tipo definido pelo usuário **MyDescriptionAttribute** que é derivado de **DescriptionAttribute** está visível e acessível dentro do assembly **System.Web.DLL**, onde ele está anexado ao método **GetLanguage**().</span><span class="sxs-lookup"><span data-stu-id="2899b-122">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3.  <span data-ttu-id="2899b-123">O tempo de execução verifica se o construtor de **MyDescriptionAttribute** está visível e acessível dentro do assembly **System.Web.DLL**.</span><span class="sxs-lookup"><span data-stu-id="2899b-123">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4.  <span data-ttu-id="2899b-124">O tempo de execução chama o construtor de **MyDescriptionAttribute** com os parâmetros do atributo personalizado e retorna o novo objeto ao chamador.</span><span class="sxs-lookup"><span data-stu-id="2899b-124">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="2899b-125">O modelo de reflexão do atributo personalizado pode causar perda de instâncias de tipos definidos pelo usuário fora do assembly no qual o tipo é definido.</span><span class="sxs-lookup"><span data-stu-id="2899b-125">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="2899b-126">Isso não é diferente dos membros na biblioteca do sistema do tempo de execução que retornam instâncias de tipos definidos pelo usuário, como <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> que retorna uma matriz de objetos **RuntimeMethodInfo**.</span><span class="sxs-lookup"><span data-stu-id="2899b-126">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="2899b-127">Para impedir que um cliente descubra informações sobre um tipo de atributo personalizado definido pelo usuário, defina os membros do tipo como confidenciais.</span><span class="sxs-lookup"><span data-stu-id="2899b-127">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="2899b-128">O exemplo a seguir demonstra a maneira básica de usar a reflexão para obter acesso a atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="2899b-128">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2899b-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2899b-129">See Also</span></span>  
 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="2899b-130">Exibindo informações de tipo</span><span class="sxs-lookup"><span data-stu-id="2899b-130">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 <span data-ttu-id="2899b-131">[Security Considerations for Reflection](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md) (Considerações sobre segurança relacionadas à reflexão)</span><span class="sxs-lookup"><span data-stu-id="2899b-131">[Security Considerations for Reflection](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)</span></span>
