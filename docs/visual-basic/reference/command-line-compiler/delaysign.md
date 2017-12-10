---
title: /delaysign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dc457a1a32048441f82976488158f223e7e3e087
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="delaysign"></a><span data-ttu-id="13076-102">/delaysign</span><span class="sxs-lookup"><span data-stu-id="13076-102">/delaysign</span></span>
<span data-ttu-id="13076-103">Especifica se o assembly será assinado total ou parcialmente.</span><span class="sxs-lookup"><span data-stu-id="13076-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13076-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13076-104">Syntax</span></span>  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="13076-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="13076-105">Arguments</span></span>  
 <span data-ttu-id="13076-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="13076-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="13076-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="13076-107">Optional.</span></span> <span data-ttu-id="13076-108">Use `/delaysign-` se você quiser um assembly totalmente assinado.</span><span class="sxs-lookup"><span data-stu-id="13076-108">Use `/delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="13076-109">Use `/delaysign+` se você deseja colocar a chave pública no assembly e reserva de espaço para o hash assinado.</span><span class="sxs-lookup"><span data-stu-id="13076-109">Use `/delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="13076-110">O padrão é `/delaysign-`.</span><span class="sxs-lookup"><span data-stu-id="13076-110">The default is `/delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13076-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="13076-111">Remarks</span></span>  
 <span data-ttu-id="13076-112">O `/delaysign` opção não tem nenhum efeito a menos que usado com [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) ou [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="13076-112">The `/delaysign` option has no effect unless used with [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="13076-113">Quando você solicita um assembly totalmente assinado, o compilador usa o hash no arquivo que contém o manifesto (metadados de assembly) e sinaliza esse hash com a chave particular.</span><span class="sxs-lookup"><span data-stu-id="13076-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="13076-114">A assinatura digital resultante é armazenada no arquivo que contém o manifesto.</span><span class="sxs-lookup"><span data-stu-id="13076-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="13076-115">Quando um assembly é assinado com atraso, o compilador não calcular e armazenar a assinatura, mas as reservas de espaço no arquivo de forma a assinatura pode ser adicionada posteriormente.</span><span class="sxs-lookup"><span data-stu-id="13076-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="13076-116">Por exemplo, usando `/delaysign+`, um desenvolvedor em uma organização pode distribuir versões de teste não assinado de um assembly que testadores podem registrar com o cache de assembly global e usar.</span><span class="sxs-lookup"><span data-stu-id="13076-116">For example, by using `/delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="13076-117">Quando o trabalho no assembly é concluído, a pessoa responsável pela chave privada da organização totalmente pode assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="13076-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="13076-118">Este compartimentalização protege a chave privada da organização contra divulgação, permitindo que todos os desenvolvedores possam trabalhar em assemblies.</span><span class="sxs-lookup"><span data-stu-id="13076-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="13076-119">Consulte [Creating and Using Strong-Named Assemblies](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) para obter mais informações sobre como assinar um assembly.</span><span class="sxs-lookup"><span data-stu-id="13076-119">See [Creating and Using Strong-Named Assemblies](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="13076-120">Para definir /delaysign no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="13076-120">To set /delaysign in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="13076-121">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="13076-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="13076-122">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="13076-122">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="13076-123">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="13076-123">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="13076-124">Clique na guia **Assinatura**.</span><span class="sxs-lookup"><span data-stu-id="13076-124">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="13076-125">Definir o valor no **atrasar a assinatura apenas** caixa.</span><span class="sxs-lookup"><span data-stu-id="13076-125">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13076-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13076-126">See Also</span></span>  
 [<span data-ttu-id="13076-127">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13076-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="13076-128">/keyfile</span><span class="sxs-lookup"><span data-stu-id="13076-128">/keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="13076-129">/keycontainer</span><span class="sxs-lookup"><span data-stu-id="13076-129">/keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [<span data-ttu-id="13076-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="13076-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
