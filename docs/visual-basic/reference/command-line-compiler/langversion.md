---
title: /langversion (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 56411df907bd5ff0416e6d0539cbe46df3b34947
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="langversion-visual-basic"></a><span data-ttu-id="19f04-102">/langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19f04-102">/langversion (Visual Basic)</span></span>
<span data-ttu-id="19f04-103">Faz com que o compilador aceitar somente a sintaxe que está incluído na versão do idioma especificado do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="19f04-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19f04-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19f04-104">Syntax</span></span>  
  
```  
/langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="19f04-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="19f04-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="19f04-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="19f04-106">Required.</span></span> <span data-ttu-id="19f04-107">A versão do idioma a ser usado durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="19f04-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="19f04-108">Os valores aceitos são `9`, `9.0`, `10`, e `10.0`.</span><span class="sxs-lookup"><span data-stu-id="19f04-108">Accepted values are `9`, `9.0`, `10`, and `10.0`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19f04-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="19f04-109">Remarks</span></span>  
 <span data-ttu-id="19f04-110">O `/langversion` opção especifica qual sintaxe aceita o compilador.</span><span class="sxs-lookup"><span data-stu-id="19f04-110">The `/langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="19f04-111">Por exemplo, se você especificar que a versão do idioma 9.0, o compilador gera erros de sintaxe que é válido somente na versão 10.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="19f04-111">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="19f04-112">Você pode usar essa opção ao desenvolver aplicativos que destino as diferentes versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="19f04-112">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="19f04-113">Por exemplo, se você estiver direcionando o .NET Framework 3.5, você pode usar esta opção para garantir que você não use a sintaxe da versão de idioma 10.0.</span><span class="sxs-lookup"><span data-stu-id="19f04-113">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="19f04-114">Você pode definir `/langversion` diretamente usando a linha de comando.</span><span class="sxs-lookup"><span data-stu-id="19f04-114">You can set `/langversion` directly only by using the command line.</span></span> <span data-ttu-id="19f04-115">Para obter mais informações, consulte [Definindo uma versão específica do .NET Framework como destino](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span><span class="sxs-lookup"><span data-stu-id="19f04-115">For more information, see [Targeting a Specific .NET Framework Version](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19f04-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="19f04-116">Example</span></span>  
 <span data-ttu-id="19f04-117">O seguinte código compila `sample.vb` para o Visual Basic 9.0.</span><span class="sxs-lookup"><span data-stu-id="19f04-117">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="19f04-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19f04-118">See Also</span></span>  
 <span data-ttu-id="19f04-119">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="19f04-119">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="19f04-120"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="19f04-120"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="19f04-121"> [Direcionamento de uma versão específica do .NET Framework](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version)</span><span class="sxs-lookup"><span data-stu-id="19f04-121"> [Targeting a Specific .NET Framework Version](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version)</span></span>
