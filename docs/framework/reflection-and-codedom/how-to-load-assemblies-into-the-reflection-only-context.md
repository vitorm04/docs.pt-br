---
title: 'Como: Carregar assemblies no contexto somente de reflexão'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, reflection-only loader context
- assemblies [.NET Framework], loading for reflection
- attributes [.NET Framework], retrieving
- assemblies [.NET Framework], reflection-only loader context
- reflection-only loader context
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dc05d27b0316c82c5314a766fcad929dc5f3698
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331046"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a><span data-ttu-id="d7c98-102">Como: Carregar assemblies no contexto somente de reflexão</span><span class="sxs-lookup"><span data-stu-id="d7c98-102">How to: Load Assemblies into the Reflection-Only Context</span></span>
<span data-ttu-id="d7c98-103">O contexto de carregamento de somente reflexão permite que você examine assemblies compilados para outras plataformas ou para outras versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7c98-103">The reflection-only load context allows you to examine assemblies compiled for other platforms or for other versions of the .NET Framework.</span></span> <span data-ttu-id="d7c98-104">O código carregado neste contexto pode apenas ser examinado, ele não pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="d7c98-104">Code loaded into this context can only be examined; it cannot be executed.</span></span> <span data-ttu-id="d7c98-105">Isso significa que os objetos não podem ser criados, pois os construtores não podem ser executados.</span><span class="sxs-lookup"><span data-stu-id="d7c98-105">This means that objects cannot be created, because constructors cannot be executed.</span></span> <span data-ttu-id="d7c98-106">Como o código não pode ser executado, as dependências não são carregadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d7c98-106">Because the code cannot be executed, dependencies are not automatically loaded.</span></span> <span data-ttu-id="d7c98-107">Se precisar examiná-las, você mesmo deverá carregá-las.</span><span class="sxs-lookup"><span data-stu-id="d7c98-107">If you need to examine them, you must load them yourself.</span></span>  
  
### <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a><span data-ttu-id="d7c98-108">Para carregar um assembly no contexto de carregamento de somente reflexão</span><span class="sxs-lookup"><span data-stu-id="d7c98-108">To load an assembly into the reflection-only load context</span></span>  
  
1. <span data-ttu-id="d7c98-109">Use a sobrecarga do método <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> para carregar o assembly dado seu nome de exibição ou o método <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> para carregar o assembly dado seu caminho.</span><span class="sxs-lookup"><span data-stu-id="d7c98-109">Use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> method overload to load the assembly given its display name, or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> method to load the assembly given its path.</span></span> <span data-ttu-id="d7c98-110">Se o assembly for uma imagem binária, use a sobrecarga do método <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="d7c98-110">If the assembly is a binary image, use the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> method overload.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7c98-111">Você não pode usar o contexto de somente reflexão para carregar uma versão de mscorlib.dll de uma versão do .NET Framework diferente da versão no contexto de execução.</span><span class="sxs-lookup"><span data-stu-id="d7c98-111">You cannot use the reflection-only context to load a version of mscorlib.dll from a version of the .NET Framework other than the version in the execution context.</span></span>  
  
2. <span data-ttu-id="d7c98-112">Se o assembly tiver dependências, o método <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> não as carregará.</span><span class="sxs-lookup"><span data-stu-id="d7c98-112">If the assembly has dependencies, the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> method does not load them.</span></span> <span data-ttu-id="d7c98-113">Se precisar examiná-las, você mesmo deverá carregá-las.</span><span class="sxs-lookup"><span data-stu-id="d7c98-113">If you need to examine them, you must load them yourself.</span></span>  
  
3. <span data-ttu-id="d7c98-114">Determine se um assembly é carregado no contexto de somente reflexão usando a propriedade <xref:System.Reflection.Assembly.ReflectionOnly%2A> do assembly.</span><span class="sxs-lookup"><span data-stu-id="d7c98-114">Determine whether an assembly is loaded into the reflection-only context by using the assembly's <xref:System.Reflection.Assembly.ReflectionOnly%2A> property.</span></span>  
  
4. <span data-ttu-id="d7c98-115">Se os atributos tiverem sido aplicados ao assembly ou aos tipos no assembly, examine esses atributos usando a classe <xref:System.Reflection.CustomAttributeData> para garantir que não seja feita nenhuma tentativa de executar o código no contexto de somente reflexão.</span><span class="sxs-lookup"><span data-stu-id="d7c98-115">If attributes have been applied to the assembly or to types in the assembly, examine those attributes by using the <xref:System.Reflection.CustomAttributeData> class to ensure that no attempt is made to execute code in the reflection-only context.</span></span> <span data-ttu-id="d7c98-116">Use a sobrecarga adequada do método <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> para obter objetos <xref:System.Reflection.CustomAttributeData> que representam os atributos aplicados a um assembly, membro, módulo ou parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d7c98-116">Use the appropriate overload of the <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method to obtain <xref:System.Reflection.CustomAttributeData> objects representing the attributes applied to an assembly, member, module, or parameter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7c98-117">Os atributos aplicados ao assembly ou ao seu conteúdo podem ser definidos no assembly ou em outro assembly carregado no contexto de somente reflexão.</span><span class="sxs-lookup"><span data-stu-id="d7c98-117">Attributes applied to the assembly or to its contents might be defined in the assembly, or they might be defined in another assembly loaded into the reflection-only context.</span></span> <span data-ttu-id="d7c98-118">Não há nenhuma maneira de dizer antecipadamente onde os atributos são definidos.</span><span class="sxs-lookup"><span data-stu-id="d7c98-118">There is no way to tell in advance where the attributes are defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7c98-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d7c98-119">Example</span></span>  
 <span data-ttu-id="d7c98-120">O exemplo de código a seguir mostra como examinar os atributos aplicados a um assembly carregado no contexto de somente reflexão.</span><span class="sxs-lookup"><span data-stu-id="d7c98-120">The following code example shows how to examine the attributes applied to an assembly loaded into the reflection-only context.</span></span>  
  
 <span data-ttu-id="d7c98-121">O exemplo de código define um atributo personalizado com dois construtores e uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="d7c98-121">The code example defines a custom attribute with two constructors and one property.</span></span> <span data-ttu-id="d7c98-122">O atributo é aplicado ao assembly, a um tipo declarado no assembly, para um método do tipo e a um parâmetro do método.</span><span class="sxs-lookup"><span data-stu-id="d7c98-122">The attribute is applied to the assembly, to a type declared in the assembly, to a method of the type, and to a parameter of the method.</span></span> <span data-ttu-id="d7c98-123">Quando executado, o próprio assembly faz seu carregamento no contexto de somente reflexão e exibe as informações sobre os atributos personalizados que foram aplicados a ele e aos tipos e os membros que ele contém.</span><span class="sxs-lookup"><span data-stu-id="d7c98-123">When executed, the assembly loads itself into the reflection-only context and displays information about the custom attributes that were applied to it and to the types and members it contains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7c98-124">Para simplificar o exemplo de código, o próprio assembly faz seu carregamento e análise.</span><span class="sxs-lookup"><span data-stu-id="d7c98-124">To simplify the code example, the assembly loads and examines itself.</span></span> <span data-ttu-id="d7c98-125">Normalmente, você não esperaria encontrar o mesmo assembly carregado no contexto de execução e no contexto de somente reflexão.</span><span class="sxs-lookup"><span data-stu-id="d7c98-125">Normally, you would not expect to find the same assembly loaded into both the execution context and the reflection-only context.</span></span>  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d7c98-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7c98-126">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
