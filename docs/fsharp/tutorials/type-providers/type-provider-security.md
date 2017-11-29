---
title: "Segurança do provedor de tipos"
description: "Saiba mais sobre a segurança de tipo de provedor em F #, incluindo como alterar as configurações de confiança para um provedor de tipo."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9c5a8a1f-5a31-490d-83c0-8beabda75c78
ms.openlocfilehash: c8f03ee90d4dce1d3484a9dfe8951d500d509a2b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="type-provider-security"></a><span data-ttu-id="39605-104">Segurança do provedor de tipos</span><span class="sxs-lookup"><span data-stu-id="39605-104">Type Provider Security</span></span>

<span data-ttu-id="39605-105">Provedores de tipos são assemblies (DLLs) referenciados pelo projeto F # ou script que contém código para se conectar a fontes de dados externas e essas informações de tipo de superfície para o ambiente do tipo F #.</span><span class="sxs-lookup"><span data-stu-id="39605-105">Type providers are assemblies (DLLs) referenced by your F# project or script that contain code to connect to external data sources and surface this type information to the F# type environment.</span></span> <span data-ttu-id="39605-106">Normalmente, o código em assemblies referenciados é executado somente quando você compila e executar o código (ou no caso de um script, envia o código para F # interativo).</span><span class="sxs-lookup"><span data-stu-id="39605-106">Typically, code in referenced assemblies is only run when you compile and then execute the code (or in the case of a script, send the code to F# Interactive).</span></span> <span data-ttu-id="39605-107">No entanto, um assembly do provedor de tipo será executado dentro do Visual Studio quando o código é simplesmente procurado no editor.</span><span class="sxs-lookup"><span data-stu-id="39605-107">However, a type provider assembly will run inside Visual Studio when the code is merely browsed in the editor.</span></span> <span data-ttu-id="39605-108">Isso ocorre porque os provedores de tipos precisam executar para adicionar informações extras no Editor, como dicas de ferramenta informações rápidas, conclusões de IntelliSense e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="39605-108">This happens because type providers need to run to add extra information to the editor, such as Quick Info tooltips, IntelliSense completions, and so on.</span></span> <span data-ttu-id="39605-109">Como resultado, há considerações de segurança adicional para o tipo de assemblies do provedor, desde que eles automaticamente executados dentro do processo do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="39605-109">As a result, there are extra security considerations for type provider assemblies, since they run automatically inside the Visual Studio process.</span></span>


## <a name="security-warning-dialog"></a><span data-ttu-id="39605-110">Caixa de diálogo de aviso de segurança</span><span class="sxs-lookup"><span data-stu-id="39605-110">Security Warning Dialog</span></span>
<span data-ttu-id="39605-111">Ao usar um assembly do provedor de tipo específico pela primeira vez, o Visual Studio exibe uma caixa de diálogo de segurança que avisa que o provedor de tipo está prestes a ser executado.</span><span class="sxs-lookup"><span data-stu-id="39605-111">When using a particular type provider assembly for the first time, Visual Studio displays a security dialog that warns you that the type provider is about to run.</span></span> <span data-ttu-id="39605-112">Antes que o Visual Studio carrega o provedor de tipo, isso lhe dá a oportunidade de decidir se você confiar nesse provedor específico.</span><span class="sxs-lookup"><span data-stu-id="39605-112">Before Visual Studio loads the type provider, it gives you the opportunity to decide if you trust this particular provider.</span></span> <span data-ttu-id="39605-113">Se você confiar na origem do provedor de tipo, em seguida, selecione "Devo confiar neste provedor de tipo".</span><span class="sxs-lookup"><span data-stu-id="39605-113">If you trust the source of the type provider, then select "I trust this type provider."</span></span> <span data-ttu-id="39605-114">Se você não confiar na origem do provedor de tipo, em seguida, selecione "Eu não confiar neste provedor de tipo".</span><span class="sxs-lookup"><span data-stu-id="39605-114">If you do not trust the source of the type provider, then select "I do not trust this type provider."</span></span> <span data-ttu-id="39605-115">Confiar o provedor permite executar dentro do Visual Studio e fornecer o IntelliSense e recursos de compilação.</span><span class="sxs-lookup"><span data-stu-id="39605-115">Trusting the provider enables it to run inside Visual Studio and provide IntelliSense and build features.</span></span> <span data-ttu-id="39605-116">Mas, se o provedor de tipos é mal-intencionado, executar seu código poderia comprometer o computador.</span><span class="sxs-lookup"><span data-stu-id="39605-116">But if the type provider itself is malicious, running its code could compromise your machine.</span></span>

<span data-ttu-id="39605-117">Se seu projeto contém o código que faz referência a provedores de tipos que você escolheu na caixa de diálogo não confiar, em seguida, em tempo de compilação, o compilador relatará um erro que indica que o provedor de tipo não é confiável.</span><span class="sxs-lookup"><span data-stu-id="39605-117">If your project contains code that references type providers that you chose in the dialog not to trust, then at compile time, the compiler will report an error that indicates that the type provider is untrusted.</span></span> <span data-ttu-id="39605-118">Quaisquer tipos que são dependentes no provedor de tipo não confiáveis são indicados por linhas onduladas vermelhas.</span><span class="sxs-lookup"><span data-stu-id="39605-118">Any types that are dependent on the untrusted type provider are indicated by red squiggles.</span></span> <span data-ttu-id="39605-119">É seguro procurar o código no editor.</span><span class="sxs-lookup"><span data-stu-id="39605-119">It is safe to browse the code in the editor.</span></span>

<span data-ttu-id="39605-120">Se você decidir alterar a configuração de confiança diretamente no Visual Studio, execute as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="39605-120">If you decide to change the trust setting directly in Visual Studio, perform the following steps.</span></span>


#### <a name="to-change-the-trust-settings-for-type-providers"></a><span data-ttu-id="39605-121">Para alterar as configurações de confiança para provedores de tipos</span><span class="sxs-lookup"><span data-stu-id="39605-121">To change the trust settings for type providers</span></span>

1. <span data-ttu-id="39605-122">Sobre o `Tools` menu, selecione `Options`e expanda o `F# Tools` nó.</span><span class="sxs-lookup"><span data-stu-id="39605-122">On the `Tools` menu, select `Options`, and expand the `F# Tools` node.</span></span>
<br />

2. <span data-ttu-id="39605-123">Selecione `Type Providers`, na lista de provedores de tipos, marque a caixa de seleção de provedores de tipos que você confia e desmarque a caixa de seleção para aqueles que você não confia.</span><span class="sxs-lookup"><span data-stu-id="39605-123">Select `Type Providers`, and in the list of type providers, select the check box for type providers you trust, and clear the check box for those you don't trust.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="39605-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39605-124">See Also</span></span>
[<span data-ttu-id="39605-125">Provedores de Tipos</span><span class="sxs-lookup"><span data-stu-id="39605-125">Type Providers</span></span>](index.md)
