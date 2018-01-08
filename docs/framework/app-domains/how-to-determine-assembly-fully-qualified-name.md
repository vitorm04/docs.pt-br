---
title: Como determinar o nome totalmente qualificado de um assembly
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 841bec105f171f3450bfc33ee9052ddb85814a5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-an-assembly39s-fully-qualified-name"></a><span data-ttu-id="85423-102">Como determinar o nome totalmente qualificado de um assembly</span><span class="sxs-lookup"><span data-stu-id="85423-102">How to: Determine an Assembly&#39;s Fully Qualified Name</span></span>
<span data-ttu-id="85423-103">Para descobrir o nome totalmente qualificado de um assembly no cache de assembly global, use a Ferramenta Cache de Assembly Global ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="85423-103">To discover the fully qualified name of an assembly in the global assembly cache, use the Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="85423-104">Consulte [Como exibir o conteúdo do cache de assembly global](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="85423-104">See [How to: View the Contents of the Global Assembly Cache](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>  
  
 <span data-ttu-id="85423-105">Para assemblies que não estão no cache de assembly global, você pode obter o nome totalmente qualificado do assembly de várias maneiras: pode usar código para produzir a saída de informações para o console ou para uma variável ou pode usar o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para examinar os metadados do assembly, que contêm o nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="85423-105">For assemblies that are not in the global assembly cache, you can get the fully qualified assembly name in a number of ways: can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
-   <span data-ttu-id="85423-106">Se o assembly já estiver carregado pelo aplicativo, você poderá recuperar o valor da propriedade <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> para obter o nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="85423-106">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="85423-107">Você pode usar essa abordagem se o assembly estiver ou não no GAC.</span><span class="sxs-lookup"><span data-stu-id="85423-107">You can use this approach whether or not the assembly is in the GAC.</span></span> <span data-ttu-id="85423-108">O exemplo fornece uma ilustração.</span><span class="sxs-lookup"><span data-stu-id="85423-108">The example provides an illustration.</span></span>  
  
-   <span data-ttu-id="85423-109">Se você souber o caminho do sistema de arquivos do assembly, poderá chamar o método (`Shared` no Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> estático para obter o nome totalmente qualificado do assembly.</span><span class="sxs-lookup"><span data-stu-id="85423-109">If you know the assembly's file system path, you can call the static (`Shared` in Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="85423-110">Este é um exemplo simples.</span><span class="sxs-lookup"><span data-stu-id="85423-110">The following is a simple example.</span></span>  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   <span data-ttu-id="85423-111">Você pode usar o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para examinar os metadados do assembly, que contêm o nome totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="85423-111">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
 <span data-ttu-id="85423-112">Para obter mais informações sobre atributos de assembly de configuração, como a versão, a cultura e o nome do assembly, consulte [Definindo atributos do assembly](../../../docs/framework/app-domains/set-assembly-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="85423-112">For more information about setting assembly attributes such as version, culture, and assembly name, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span> <span data-ttu-id="85423-113">Para obter mais informações sobre como atribuir um nome forte a um assembly, consulte [Criando e usando assemblies de nomes fortes](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="85423-113">For more information about giving an assembly a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="85423-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="85423-114">Example</span></span>  
 <span data-ttu-id="85423-115">O exemplo de código a seguir mostra como exibir o nome totalmente qualificado de um assembly que contém uma classe especificada no console.</span><span class="sxs-lookup"><span data-stu-id="85423-115">The following code example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="85423-116">Como ele recupera o nome de um assembly que o aplicativo já carregou, não importa se o assembly está no GAC.</span><span class="sxs-lookup"><span data-stu-id="85423-116">Because it retrieves the name of an assembly that the app has already loaded, it does not matter whether the assembly is in the GAC.</span></span>  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="85423-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85423-117">See Also</span></span>  
 [<span data-ttu-id="85423-118">Nomes de assembly</span><span class="sxs-lookup"><span data-stu-id="85423-118">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 [<span data-ttu-id="85423-119">Criação de assemblies</span><span class="sxs-lookup"><span data-stu-id="85423-119">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="85423-120">Criar e usar assemblies de nomes fortes</span><span class="sxs-lookup"><span data-stu-id="85423-120">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [<span data-ttu-id="85423-121">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="85423-121">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="85423-122">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="85423-122">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="85423-123">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="85423-123">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
