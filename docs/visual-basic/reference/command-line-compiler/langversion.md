---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 5f59f1c4c269a52131a324bbd2bfbe817ab794a4
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197092"
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="48dde-102">-langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48dde-102">-langversion (Visual Basic)</span></span>
<span data-ttu-id="48dde-103">Faz com que o compilador aceite apenas a sintaxe que está incluída na versão especificada do idioma de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="48dde-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48dde-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48dde-104">Syntax</span></span>  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="48dde-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="48dde-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="48dde-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="48dde-106">Required.</span></span> <span data-ttu-id="48dde-107">A versão de idioma a ser usada durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="48dde-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="48dde-108">Os valores aceitos são `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` e `latest`.</span><span class="sxs-lookup"><span data-stu-id="48dde-108">Accepted values are `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` and `latest`.</span></span>

 <span data-ttu-id="48dde-109">Qualquer um dos números inteiros também pode ser especificado usando `.0` como a versão secundária, por exemplo, `11.0`.</span><span class="sxs-lookup"><span data-stu-id="48dde-109">Any of the whole numbers may also be specified using `.0` as the minor version, for example, `11.0`.</span></span>

 <span data-ttu-id="48dde-110">Você pode ver a lista de todos os valores possíveis especificando `-langversion:?` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="48dde-110">You can see the list of all possible values by specifying `-langversion:?` on the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48dde-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="48dde-111">Remarks</span></span>  
 <span data-ttu-id="48dde-112">A opção `-langversion` especifica a sintaxe aceita pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="48dde-112">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="48dde-113">Por exemplo, se você especificar que a versão do idioma é 9,0, o compilador gerará erros de sintaxe válida somente na versão 10,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="48dde-113">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="48dde-114">Você pode usar essa opção ao desenvolver aplicativos direcionados a diferentes versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48dde-114">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="48dde-115">Por exemplo, se você estiver direcionando .NET Framework 3,5, poderá usar essa opção para garantir que não use a sintaxe da versão de linguagem 10,0.</span><span class="sxs-lookup"><span data-stu-id="48dde-115">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="48dde-116">Você pode definir `-langversion` diretamente usando a linha de comando.</span><span class="sxs-lookup"><span data-stu-id="48dde-116">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="48dde-117">Para obter mais informações, consulte [Definindo uma Versão Específica do .NET Framework como Destino](/visualstudio/ide/visual-studio-multi-targeting-overview).</span><span class="sxs-lookup"><span data-stu-id="48dde-117">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/visual-studio-multi-targeting-overview).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48dde-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48dde-118">Example</span></span>  
 <span data-ttu-id="48dde-119">O código a seguir compila `sample.vb` para Visual Basic 9,0.</span><span class="sxs-lookup"><span data-stu-id="48dde-119">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="48dde-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48dde-120">See also</span></span>

- [<span data-ttu-id="48dde-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="48dde-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="48dde-122">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="48dde-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="48dde-123">Direcionamento de uma versão específica do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="48dde-123">Targeting a Specific .NET Framework Version</span></span>](/visualstudio/ide/visual-studio-multi-targeting-overview)
