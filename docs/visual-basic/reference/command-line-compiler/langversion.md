---
title: /langversion (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cfe91588471cc8410b25addea8d66a0388c9c5be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="langversion-visual-basic"></a><span data-ttu-id="d33d7-102">/langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d33d7-102">/langversion (Visual Basic)</span></span>
<span data-ttu-id="d33d7-103">Faz com que o compilador aceitar somente a sintaxe que está incluída na versão de idioma especificado do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d33d7-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d33d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d33d7-104">Syntax</span></span>  
  
```  
/langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="d33d7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d33d7-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="d33d7-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d33d7-106">Required.</span></span> <span data-ttu-id="d33d7-107">A versão do idioma a ser usado durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="d33d7-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="d33d7-108">Os valores aceitos são `9`, `9.0`, `10`, e `10.0`.</span><span class="sxs-lookup"><span data-stu-id="d33d7-108">Accepted values are `9`, `9.0`, `10`, and `10.0`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d33d7-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d33d7-109">Remarks</span></span>  
 <span data-ttu-id="d33d7-110">O `/langversion` opção especifica que o compilador aceita de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="d33d7-110">The `/langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="d33d7-111">Por exemplo, se você especificar que a versão de idioma é 9.0, o compilador gera erros de sintaxe que é válido somente na versão 10.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="d33d7-111">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="d33d7-112">Você pode usar essa opção ao desenvolver aplicativos que destino as diferentes versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d33d7-112">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="d33d7-113">Por exemplo, se você estiver direcionando o .NET Framework 3.5, você pode usar essa opção para garantir que você não use a sintaxe da versão de idioma 10.0.</span><span class="sxs-lookup"><span data-stu-id="d33d7-113">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="d33d7-114">Você pode definir `/langversion` diretamente usando a linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d33d7-114">You can set `/langversion` directly only by using the command line.</span></span> <span data-ttu-id="d33d7-115">Para obter mais informações, consulte [Definindo uma Versão Específica do .NET Framework como Destino](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span><span class="sxs-lookup"><span data-stu-id="d33d7-115">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d33d7-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d33d7-116">Example</span></span>  
 <span data-ttu-id="d33d7-117">O código a seguir compila `sample.vb` para o Visual Basic 9.0.</span><span class="sxs-lookup"><span data-stu-id="d33d7-117">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d33d7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d33d7-118">See Also</span></span>  
 [<span data-ttu-id="d33d7-119">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d33d7-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d33d7-120">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="d33d7-120">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="d33d7-121">Direcionamento de uma versão específica do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d33d7-121">Targeting a Specific .NET Framework Version</span></span>](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
