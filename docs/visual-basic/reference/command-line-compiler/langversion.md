---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9b91bf8efa6fabd21d257e51062dc881ab288f5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="9d7f5-102">-langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d7f5-102">-langversion (Visual Basic)</span></span>
<span data-ttu-id="9d7f5-103">Faz com que o compilador aceitar somente a sintaxe que está incluída na versão de idioma especificado do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d7f5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d7f5-104">Syntax</span></span>  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="9d7f5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9d7f5-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="9d7f5-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-106">Required.</span></span> <span data-ttu-id="9d7f5-107">A versão do idioma a ser usado durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="9d7f5-108">Os valores aceitos são `9`, `9.0`, `10`, e `10.0`.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-108">Accepted values are `9`, `9.0`, `10`, and `10.0`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d7f5-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d7f5-109">Remarks</span></span>  
 <span data-ttu-id="9d7f5-110">O `-langversion` opção especifica que o compilador aceita de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-110">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="9d7f5-111">Por exemplo, se você especificar que a versão de idioma é 9.0, o compilador gera erros de sintaxe que é válido somente na versão 10.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-111">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="9d7f5-112">Você pode usar essa opção ao desenvolver aplicativos que destino as diferentes versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-112">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="9d7f5-113">Por exemplo, se você estiver direcionando o .NET Framework 3.5, você pode usar essa opção para garantir que você não use a sintaxe da versão de idioma 10.0.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-113">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="9d7f5-114">Você pode definir `-langversion` diretamente usando a linha de comando.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-114">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="9d7f5-115">Para obter mais informações, consulte [Definindo uma Versão Específica do .NET Framework como Destino](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span><span class="sxs-lookup"><span data-stu-id="9d7f5-115">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d7f5-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d7f5-116">Example</span></span>  
 <span data-ttu-id="9d7f5-117">O código a seguir compila `sample.vb` para o Visual Basic 9.0.</span><span class="sxs-lookup"><span data-stu-id="9d7f5-117">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d7f5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d7f5-118">See Also</span></span>  
 [<span data-ttu-id="9d7f5-119">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d7f5-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9d7f5-120">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d7f5-120">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="9d7f5-121">Direcionamento de uma versão específica do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9d7f5-121">Targeting a Specific .NET Framework Version</span></span>](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
