---
title: "Não é possível gravar no arquivo de saída &quot;&lt;filename&gt;&quot;: &lt;erro&gt; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31019
- bc31019
dev_langs:
- VB
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
caps.latest.revision: 10
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
ms.openlocfilehash: 0822a732390f308b5f8f1f1431299552fb876e74
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a><span data-ttu-id="393cc-102">Não é possível gravar no arquivo de saída '&lt;filename&gt;': &lt;erro&gt;</span><span class="sxs-lookup"><span data-stu-id="393cc-102">Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt;</span></span>
<span data-ttu-id="393cc-103">Ocorreu um problema na criação do arquivo.</span><span class="sxs-lookup"><span data-stu-id="393cc-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="393cc-104">Não foi possível abrir um arquivo de saída para gravação.</span><span class="sxs-lookup"><span data-stu-id="393cc-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="393cc-105">O arquivo (ou a pasta que contém o arquivo) pode estar aberto para uso exclusivo por outro processo ou pode ter seu atributo definido como somente leitura.</span><span class="sxs-lookup"><span data-stu-id="393cc-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="393cc-106">Algumas situações comuns em que um arquivo fica aberto exclusivamente são quando:</span><span class="sxs-lookup"><span data-stu-id="393cc-106">Common situations where a file is opened exclusively are:</span></span>  
  
-   <span data-ttu-id="393cc-107">O aplicativo está em execução e usando os arquivos dele.</span><span class="sxs-lookup"><span data-stu-id="393cc-107">The application is already running and using its files.</span></span> <span data-ttu-id="393cc-108">Para resolver esse problema, verifique se o aplicativo não está em execução.</span><span class="sxs-lookup"><span data-stu-id="393cc-108">To solve this problem, make sure that the application is not running.</span></span>  
  
-   <span data-ttu-id="393cc-109">Outro aplicativo abriu o arquivo.</span><span class="sxs-lookup"><span data-stu-id="393cc-109">Another application has opened the file.</span></span> <span data-ttu-id="393cc-110">Para resolver esse problema, verifique se nenhum outro aplicativo está acessando os arquivos.</span><span class="sxs-lookup"><span data-stu-id="393cc-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="393cc-111">Nem sempre é óbvio qual aplicativo está acessando seus arquivos. Nesse caso, reiniciar o computador pode ser o caminho mais fácil para encerrar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="393cc-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="393cc-112">Se apenas um dos arquivos de saída do projeto estiver marcado como somente leitura, esta exceção será acionada.</span><span class="sxs-lookup"><span data-stu-id="393cc-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="393cc-113">**ID do erro:** BC31019</span><span class="sxs-lookup"><span data-stu-id="393cc-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="393cc-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="393cc-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="393cc-115">Compile o programa novamente para verificar se o erro persiste.</span><span class="sxs-lookup"><span data-stu-id="393cc-115">Compile the program again to see if the error recurs.</span></span>  
  
2.  <span data-ttu-id="393cc-116">Se o erro persistir, salve seu trabalho e reinicie o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)].</span><span class="sxs-lookup"><span data-stu-id="393cc-116">If the error continues, save your work and restart [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)].</span></span>  
  
3.  <span data-ttu-id="393cc-117">Se o erro persistir, reinicie o computador.</span><span class="sxs-lookup"><span data-stu-id="393cc-117">If the error continues, restart the computer.</span></span>  
  
4.  <span data-ttu-id="393cc-118">Se o erro persistir, reinstale o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="393cc-118">If the error recurs, reinstall [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
5.  <span data-ttu-id="393cc-119">Se o erro persistir após a reinstalação, notifique o Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="393cc-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="393cc-120">Para verificar atributos de arquivo no Explorador de Arquivos</span><span class="sxs-lookup"><span data-stu-id="393cc-120">To check file attributes in File Explorer</span></span>  
  
1.  <span data-ttu-id="393cc-121">Abra a pasta que lhe interessa.</span><span class="sxs-lookup"><span data-stu-id="393cc-121">Open the folder you are interested in.</span></span>  
  
2.  <span data-ttu-id="393cc-122">Clique o **exibições** ícone e escolha **detalhes**.</span><span class="sxs-lookup"><span data-stu-id="393cc-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3.  <span data-ttu-id="393cc-123">Clique com botão direito no cabeçalho da coluna e escolha **atributos** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="393cc-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="393cc-124">Para alterar os atributos de um arquivo ou pasta</span><span class="sxs-lookup"><span data-stu-id="393cc-124">To change the attributes of a file or folder</span></span>  
  
1.  <span data-ttu-id="393cc-125">Em **File Explorer**, com o botão direito no arquivo ou pasta e escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="393cc-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="393cc-126">No **atributos** seção o **geral** guia, desmarque o **somente leitura** caixa.</span><span class="sxs-lookup"><span data-stu-id="393cc-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3.  <span data-ttu-id="393cc-127">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="393cc-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="393cc-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="393cc-128">See Also</span></span>  
 [<span data-ttu-id="393cc-129">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="393cc-129">Talk to Us</span></span>](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
