---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: d1307603ebc06b4eb4c3786f1cd2fb432c0cf636
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360456"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="3135b-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3135b-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="3135b-103">Suprime a exibição da faixa de direitos autorais e as mensagens informativas durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="3135b-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3135b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3135b-104">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="3135b-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="3135b-105">Remarks</span></span>  
 <span data-ttu-id="3135b-106">Se você especificar `-nologo` , o compilador não exibirá uma faixa de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="3135b-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="3135b-107">Por padrão, `-nologo` não está em vigor.</span><span class="sxs-lookup"><span data-stu-id="3135b-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3135b-108">A `-nologo` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="3135b-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3135b-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3135b-109">Example</span></span>  
 <span data-ttu-id="3135b-110">O código a seguir compila `T2.vb` e não exibe uma faixa de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="3135b-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3135b-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="3135b-111">See also</span></span>

- [<span data-ttu-id="3135b-112">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3135b-112">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3135b-113">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="3135b-113">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
