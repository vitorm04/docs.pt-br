---
title: 'Como: Carregar assemblies em um domínio do aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d785ae9b3bce0b5c77414057ef063d6e9d3e14a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593584"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="205c7-102">Como: Carregar assemblies em um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="205c7-102">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="205c7-103">Há várias maneiras de carregar um assembly em um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="205c7-103">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="205c7-104">A maneira recomendada é usar o método <xref:System.Reflection.Assembly.Load%2A> `static` (`Shared` no Visual Basic) da classe <xref:System.Reflection.Assembly?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="205c7-104">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="205c7-105">Outras maneiras que os assemblies podem ser carregados incluem:</span><span class="sxs-lookup"><span data-stu-id="205c7-105">Other ways assemblies can be loaded include:</span></span>  
  
- <span data-ttu-id="205c7-106">O método <xref:System.Reflection.Assembly.LoadFrom%2A> da classe <xref:System.Reflection.Assembly> carrega um assembly dado seu local do arquivo.</span><span class="sxs-lookup"><span data-stu-id="205c7-106">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="205c7-107">O carregamento de assemblies com esse método usa um contexto de carga diferente.</span><span class="sxs-lookup"><span data-stu-id="205c7-107">Loading assemblies with this method uses a different load context.</span></span>  
  
- <span data-ttu-id="205c7-108">Os métodos <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> e <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> carregam um assembly no contexto de somente reflexão.</span><span class="sxs-lookup"><span data-stu-id="205c7-108">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="205c7-109">Os assemblies carregados neste contexto podem ser examinados, mas não executados, permitindo o exame dos assemblies que visam outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="205c7-109">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="205c7-110">Confira [Como carregar assemblies no contexto somente de reflexão](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="205c7-110">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="205c7-111">O contexto de somente reflexão é uma novidade no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="205c7-111">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
- <span data-ttu-id="205c7-112">Métodos como <xref:System.AppDomain.CreateInstance%2A> e <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> da classe <xref:System.AppDomain> podem carregar assemblies em um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="205c7-112">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
- <span data-ttu-id="205c7-113">O método <xref:System.Type.GetType%2A> da classe <xref:System.Type> pode carregar assemblies.</span><span class="sxs-lookup"><span data-stu-id="205c7-113">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
- <span data-ttu-id="205c7-114">O método <xref:System.AppDomain.Load%2A> da classe <xref:System.AppDomain?displayProperty=nameWithType> pode carregar assemblies, mas ele é usado principalmente para a interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="205c7-114">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=nameWithType> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="205c7-115">Ele não deve ser usado para carregar assemblies em um domínio do aplicativo diferente do domínio do aplicativo do qual ele foi chamado.</span><span class="sxs-lookup"><span data-stu-id="205c7-115">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="205c7-116">A partir do .NET Framework versão 2.0, o tempo de execução não carregará um assembly que foi compilado com uma versão do .NET Framework que tenha um número de versão mais alto do que o tempo de execução atualmente carregado.</span><span class="sxs-lookup"><span data-stu-id="205c7-116">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="205c7-117">Isso vale para a combinação dos componentes principal e secundário do número de versão.</span><span class="sxs-lookup"><span data-stu-id="205c7-117">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="205c7-118">Você pode especificar a maneira como o JIT (Just-In-Time) compilou o código dos assemblies carregados é compartilhado entre os domínios do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="205c7-118">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="205c7-119">Para obter mais informações, confira [Domínios do aplicativo e assemblies](application-domains.md#application-domains-and-assemblies).</span><span class="sxs-lookup"><span data-stu-id="205c7-119">For more information, see [Application domains and assemblies](application-domains.md#application-domains-and-assemblies).</span></span>  
  
## <a name="example"></a><span data-ttu-id="205c7-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="205c7-120">Example</span></span>  
 <span data-ttu-id="205c7-121">O código a seguir carrega um assembly chamado "example.exe" ou "example.dll" para o domínio de aplicativo atual, obtém um tipo chamado `Example` do assembly, obtém um método sem parâmetros chamado `MethodA` para esse tipo e executa o método.</span><span class="sxs-lookup"><span data-stu-id="205c7-121">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="205c7-122">Para encontrar uma discussão completa sobre como obter as informações de um assembly carregado, consulte [Dynamically Loading and Using Types](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md) (Carregando e usando tipos dinamicamente).</span><span class="sxs-lookup"><span data-stu-id="205c7-122">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="205c7-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="205c7-123">See also</span></span>

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [<span data-ttu-id="205c7-124">Programação com domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="205c7-124">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="205c7-125">Reflexão</span><span class="sxs-lookup"><span data-stu-id="205c7-125">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)
- [<span data-ttu-id="205c7-126">Usar domínios do aplicativo</span><span class="sxs-lookup"><span data-stu-id="205c7-126">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
- [<span data-ttu-id="205c7-127">Como: Carregar assemblies no contexto somente de reflexão</span><span class="sxs-lookup"><span data-stu-id="205c7-127">How to: Load Assemblies into the Reflection-Only Context</span></span>](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [<span data-ttu-id="205c7-128">Domínios do aplicativo e assemblies</span><span class="sxs-lookup"><span data-stu-id="205c7-128">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
