---
title: /Main | Documentos do Microsoft
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
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: 19
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
ms.openlocfilehash: 61aa78e131ba8903035f630a540f49848f1acd3f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="main"></a><span data-ttu-id="f72fc-102">/main</span><span class="sxs-lookup"><span data-stu-id="f72fc-102">/main</span></span>
<span data-ttu-id="f72fc-103">Especifica a classe ou o módulo que contém o procedimento `Sub Main`.</span><span class="sxs-lookup"><span data-stu-id="f72fc-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f72fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f72fc-104">Syntax</span></span>  
  
```  
/main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="f72fc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f72fc-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="f72fc-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f72fc-106">Required.</span></span> <span data-ttu-id="f72fc-107">Um total de qualificação para a classe ou módulo que contém o `Sub Main` procedimento a ser chamado quando o programa for iniciado.</span><span class="sxs-lookup"><span data-stu-id="f72fc-107">A full qualification to the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="f72fc-108">Isso pode estar no formato **/main:module** ou **/Main**.</span><span class="sxs-lookup"><span data-stu-id="f72fc-108">This may be in the form **/main:module** or **/main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f72fc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f72fc-109">Remarks</span></span>  
 <span data-ttu-id="f72fc-110">Use esta opção quando você cria um arquivo executável ou programa executável do Windows.</span><span class="sxs-lookup"><span data-stu-id="f72fc-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="f72fc-111">Se o **/principal** opção for omitida, o compilador procura por um arquivo compartilhado `Sub Main` em todas as classes públicas e módulos.</span><span class="sxs-lookup"><span data-stu-id="f72fc-111">If the **/main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="f72fc-112">Consulte [procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) para uma discussão sobre as diversas formas dos `Main` procedimento.</span><span class="sxs-lookup"><span data-stu-id="f72fc-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="f72fc-113">Quando `location` é uma classe que herda de <xref:System.Windows.Forms.Form>, o compilador fornece um padrão `Main` que inicia o aplicativo se a classe possui nenhum procedimento `Main` procedimento.</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="f72fc-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="f72fc-114">Isso lhe permite compilar código na linha de comando que foi criado no ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="f72fc-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 <span data-ttu-id="f72fc-115">[!code-vb[VbVbalrCompiler n º&16;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f72fc-115">[!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]</span></span>  
  
### <a name="to-set-main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="f72fc-116">Para definir/principal no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="f72fc-116">To set /main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="f72fc-117">Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="f72fc-117">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f72fc-118">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="f72fc-118">On the **Project** menu, click **Properties**.</span></span>  
  
     <span data-ttu-id="f72fc-119">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="f72fc-119">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="f72fc-120">Clique o **aplicativo** guia.</span><span class="sxs-lookup"><span data-stu-id="f72fc-120">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="f72fc-121">Verifique se o **estrutura do aplicativo ativar** caixa de seleção não estiver marcada.</span><span class="sxs-lookup"><span data-stu-id="f72fc-121">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="f72fc-122">Modificar o valor de **o objeto de inicialização** caixa.</span><span class="sxs-lookup"><span data-stu-id="f72fc-122">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f72fc-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f72fc-123">Example</span></span>  
 <span data-ttu-id="f72fc-124">O seguinte código compila `T2.vb` e `T3.vb`, especificando que o `Sub Main` procedimento será encontrado na `Test2` classe.</span><span class="sxs-lookup"><span data-stu-id="f72fc-124">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="f72fc-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f72fc-125">See Also</span></span>  
 <span data-ttu-id="f72fc-126">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="f72fc-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="f72fc-127"> [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="f72fc-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="f72fc-128"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="f72fc-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="f72fc-129"> [NIB: versão do Visual Basic do Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c) </span><span class="sxs-lookup"><span data-stu-id="f72fc-129"> [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c) </span></span>  
<span data-ttu-id="f72fc-130"> [Procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)</span><span class="sxs-lookup"><span data-stu-id="f72fc-130"> [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)</span></span>
