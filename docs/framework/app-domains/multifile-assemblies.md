---
title: Assemblies de vários arquivos
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f319ef94a5a0f1a5239a2f506386dbc15f0505ef
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48846416"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="9a4a7-102">Assemblies de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="9a4a7-102">Multifile Assemblies</span></span>

<span data-ttu-id="9a4a7-103">Você pode criar assemblies de vários arquivos usando os compiladores de linha de comando ou o Visual Studio com o Visual C++.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-103">You can create multifile assemblies using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="9a4a7-104">Um arquivo no assembly deve conter o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="9a4a7-105">Um assembly que inicia um aplicativo também deve conter um ponto de entrada, como um método Main ou WinMain.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-105">An assembly that starts an application must also contain an entry point, such as a Main or WinMain method.</span></span>

<span data-ttu-id="9a4a7-106">Por exemplo, suponha que você tenha um aplicativo que contém dois módulos de código, Client.cs e Stringer.cs.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-106">For example, suppose you have an application that contains two code modules, Client.cs and Stringer.cs.</span></span> <span data-ttu-id="9a4a7-107">Stringer.cs cria o namespace `myStringer` que é referenciado pelo código em Client.cs.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-107">Stringer.cs creates the `myStringer` namespace that is referenced by the code in Client.cs.</span></span> <span data-ttu-id="9a4a7-108">Client.cs contém o método `Main`, que é o ponto de entrada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-108">Client.cs contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="9a4a7-109">Neste exemplo, você compila os dois módulos de código e cria um terceiro arquivo que contém o manifesto do assembly, que inicia o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="9a4a7-110">O manifesto do assembly faz referência aos módulos `Client` e `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-110">The assembly manifest references both the `Client` and `Stringer` modules.</span></span>

> [!NOTE]
> <span data-ttu-id="9a4a7-111">Os assemblies de vários arquivos podem ter apenas um ponto de entrada, mesmo que o assembly tenha vários módulos de código.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="9a4a7-112">Existem vários motivos que levam você a querer criar um assembly de vários arquivos:</span><span class="sxs-lookup"><span data-stu-id="9a4a7-112">There are several reasons you might want to create a multifile assembly:</span></span>

-   <span data-ttu-id="9a4a7-113">Para combinar módulos escritos em linguagens diferentes.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-113">To combine modules written in different languages.</span></span> <span data-ttu-id="9a4a7-114">Essa é a razão mais comum para a criação de um assembly de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-114">This is the most common reason for creating a multifile assembly.</span></span>

-   <span data-ttu-id="9a4a7-115">Para otimizar o download de um aplicativo colocando tipos raramente usados em um módulo que é baixado apenas quando necessário.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9a4a7-116">Se você estiver criando aplicativos que serão baixados usando a marca `<object>` com o Microsoft Internet Explorer, é importante criar assemblies de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="9a4a7-117">Nesse cenário, você cria um arquivo separado do seus módulos de código que contenha somente o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="9a4a7-118">O Internet Explorer baixa o manifesto do assembly primeiro e, em seguida, cria threads de trabalho para baixar quaisquer módulos adicionais ou assemblies necessários.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="9a4a7-119">Enquanto o arquivo que contém o manifesto do assembly estiver sendo baixado, o Internet Explorer não responderá à entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="9a4a7-120">Quanto menor o arquivo que contém o manifesto do assembly, menos tempo o Internet Explorer ficará sem responder.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

-   <span data-ttu-id="9a4a7-121">Para combinar módulos de código escritos por vários desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="9a4a7-122">Embora cada desenvolvedor possa compilar cada módulo de código em um assembly, isso pode forçar alguns tipos a serem expostos publicamente, que não o seriam se todos os módulos fossem colocados em um assembly de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="9a4a7-123">Depois de criar o assembly, você pode assinar o arquivo que contém o manifesto do assembly (e, portanto, o assembly) ou pode dar um nome forte ao arquivo (e ao assembly) e colocá-lo no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="9a4a7-123">Once you create the assembly, you can sign the file that contains the assembly manifest (and hence the assembly), or you can give the file (and the assembly) a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a4a7-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a4a7-124">See Also</span></span>

- [<span data-ttu-id="9a4a7-125">Como Compilar um Assembly de Vários Arquivos</span><span class="sxs-lookup"><span data-stu-id="9a4a7-125">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="9a4a7-126">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="9a4a7-126">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)