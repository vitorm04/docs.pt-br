---
title: "entrada/saída (Visual Basic) | Documentos do Microsoft"
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
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
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
ms.openlocfilehash: 489a9015718a581c793cd1217ba073625929daf3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="out-visual-basic"></a><span data-ttu-id="d779f-102">/out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d779f-102">/out (Visual Basic)</span></span>
<span data-ttu-id="d779f-103">Especifica o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="d779f-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d779f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d779f-104">Syntax</span></span>  
  
```  
/out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="d779f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d779f-105">Arguments</span></span>  
  
|<span data-ttu-id="d779f-106">Termo</span><span class="sxs-lookup"><span data-stu-id="d779f-106">Term</span></span>|<span data-ttu-id="d779f-107">Definição</span><span class="sxs-lookup"><span data-stu-id="d779f-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="d779f-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d779f-108">Required.</span></span> <span data-ttu-id="d779f-109">O nome do arquivo de saída que o compilador cria.</span><span class="sxs-lookup"><span data-stu-id="d779f-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="d779f-110">Se o nome do arquivo contém um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="d779f-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d779f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d779f-111">Remarks</span></span>  
 <span data-ttu-id="d779f-112">Especifique o nome completo e a extensão do arquivo a ser criado.</span><span class="sxs-lookup"><span data-stu-id="d779f-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="d779f-113">Se você não fizer isso, o arquivo de .exe leva seu nome a partir do arquivo de código-fonte que contém o `Sub Main` procedimento e o arquivo. dll leva seu nome do primeiro arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="d779f-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="d779f-114">Se você especificar um nome de arquivo sem uma extensão .exe ou. dll, o compilador adiciona automaticamente a extensão para você, dependendo do valor especificado para o `/target` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="d779f-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `/target` compiler option.</span></span>  
  
|<span data-ttu-id="d779f-115">Para configurar /out no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d779f-115">To set /out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d779f-116">1.  Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="d779f-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d779f-117">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d779f-117">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="d779f-118">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="d779f-118">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="d779f-119">2.  Clique o **aplicativo** guia.</span><span class="sxs-lookup"><span data-stu-id="d779f-119">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="d779f-120">3.  Modificar o valor de **nome do Assembly** caixa.</span><span class="sxs-lookup"><span data-stu-id="d779f-120">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d779f-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d779f-121">Example</span></span>  
 <span data-ttu-id="d779f-122">O seguinte código compila `T2.vb` e cria o arquivo de saída `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="d779f-122">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="d779f-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d779f-123">See Also</span></span>  
 <span data-ttu-id="d779f-124">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="d779f-124">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="d779f-125"> [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="d779f-125"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="d779f-126"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="d779f-126"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
