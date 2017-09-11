---
title: /codepage (Visual Basic) | Documentos do Microsoft
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
- /codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: 17
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
ms.openlocfilehash: 6f4919bc4fc8eda700edbd80fead5b5d9fe0dba1
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="codepage-visual-basic"></a><span data-ttu-id="bf1a5-102">/codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf1a5-102">/codepage (Visual Basic)</span></span>
<span data-ttu-id="bf1a5-103">Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação.</span><span class="sxs-lookup"><span data-stu-id="bf1a5-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf1a5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf1a5-104">Syntax</span></span>  
  
```  
/codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="bf1a5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bf1a5-105">Arguments</span></span>  
  
|<span data-ttu-id="bf1a5-106">Termo</span><span class="sxs-lookup"><span data-stu-id="bf1a5-106">Term</span></span>|<span data-ttu-id="bf1a5-107">Definição</span><span class="sxs-lookup"><span data-stu-id="bf1a5-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="bf1a5-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bf1a5-108">Required.</span></span> <span data-ttu-id="bf1a5-109">O compilador usa a página de código especificada pela `id` para interpretar a codificação dos arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="bf1a5-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf1a5-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf1a5-110">Remarks</span></span>  
 <span data-ttu-id="bf1a5-111">Para compilar o código-fonte salvo com uma codificação específica, você pode usar `/codepage` para especificar qual página de código deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="bf1a5-111">To compile source code saved with a specific encoding, you can use `/codepage` to specify which code page should be used.</span></span> <span data-ttu-id="bf1a5-112">O `/codepage` opção se aplica a todos os arquivos de código-fonte na sua compilação.</span><span class="sxs-lookup"><span data-stu-id="bf1a5-112">The `/codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="bf1a5-113">Para obter mais informações, consulte [codificação de caracteres no .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span><span class="sxs-lookup"><span data-stu-id="bf1a5-113">For more information, see [Character Encoding in the .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="bf1a5-114">O `/codepage` opção não é necessária se os arquivos de código-fonte foram salvos com o atual página de código ANSI, Unicode ou UTF-8 com uma assinatura.</span><span class="sxs-lookup"><span data-stu-id="bf1a5-114">The `/codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="bf1a5-115">salva todos os arquivos de código-fonte com a página de código ANSI atual por padrão, a menos que o usuário especifique outra codificação no **codificação** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="bf1a5-115"> saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="bf1a5-116">usa o **codificação** caixa de diálogo para abrir arquivos de código-fonte salvos com uma página de código diferente.</span><span class="sxs-lookup"><span data-stu-id="bf1a5-116"> uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf1a5-117">O `/codepage` opção não está disponível de dentro do [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ambiente de desenvolvimento; está disponível apenas quando se compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="bf1a5-117">The `/codepage` option is not available from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf1a5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf1a5-118">See Also</span></span>  
 [<span data-ttu-id="bf1a5-119">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bf1a5-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
