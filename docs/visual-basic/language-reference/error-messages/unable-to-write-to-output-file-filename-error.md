---
title: 'Não é possível gravar no arquivo de saída &#39; &lt;filename&gt;&#39;: &lt;erro&gt;'
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: e8fbfd54782e601595712035827ea346d1dbf500
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597504"
---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a><span data-ttu-id="35c64-102">Não é possível gravar no arquivo de saída &#39; &lt;filename&gt;&#39;: &lt;erro&gt;</span><span class="sxs-lookup"><span data-stu-id="35c64-102">Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt;</span></span>
<span data-ttu-id="35c64-103">Ocorreu um problema na criação do arquivo.</span><span class="sxs-lookup"><span data-stu-id="35c64-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="35c64-104">Não foi possível abrir um arquivo de saída para gravação.</span><span class="sxs-lookup"><span data-stu-id="35c64-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="35c64-105">O arquivo (ou a pasta que contém o arquivo) pode estar aberto para uso exclusivo por outro processo ou pode ter seu atributo definido como somente leitura.</span><span class="sxs-lookup"><span data-stu-id="35c64-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="35c64-106">Algumas situações comuns em que um arquivo fica aberto exclusivamente são quando:</span><span class="sxs-lookup"><span data-stu-id="35c64-106">Common situations where a file is opened exclusively are:</span></span>  
  
-   <span data-ttu-id="35c64-107">O aplicativo está em execução e usando os arquivos dele.</span><span class="sxs-lookup"><span data-stu-id="35c64-107">The application is already running and using its files.</span></span> <span data-ttu-id="35c64-108">Para resolver esse problema, verifique se o aplicativo não está em execução.</span><span class="sxs-lookup"><span data-stu-id="35c64-108">To solve this problem, make sure that the application is not running.</span></span>  
  
-   <span data-ttu-id="35c64-109">Outro aplicativo abriu o arquivo.</span><span class="sxs-lookup"><span data-stu-id="35c64-109">Another application has opened the file.</span></span> <span data-ttu-id="35c64-110">Para resolver esse problema, verifique se nenhum outro aplicativo está acessando os arquivos.</span><span class="sxs-lookup"><span data-stu-id="35c64-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="35c64-111">Nem sempre é óbvio qual aplicativo está acessando seus arquivos. Nesse caso, reiniciar o computador pode ser o caminho mais fácil para encerrar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="35c64-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="35c64-112">Se apenas um dos arquivos de saída do projeto estiver marcado como somente leitura, esta exceção será acionada.</span><span class="sxs-lookup"><span data-stu-id="35c64-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="35c64-113">**ID do erro:** BC31019</span><span class="sxs-lookup"><span data-stu-id="35c64-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="35c64-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="35c64-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="35c64-115">Compile o programa novamente para verificar se o erro persiste.</span><span class="sxs-lookup"><span data-stu-id="35c64-115">Compile the program again to see if the error recurs.</span></span>  
  
2.  <span data-ttu-id="35c64-116">Se o erro persistir, salve seu trabalho e reinicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="35c64-116">If the error continues, save your work and restart Visual Studio.</span></span>  
  
3.  <span data-ttu-id="35c64-117">Se o erro persistir, reinicie o computador.</span><span class="sxs-lookup"><span data-stu-id="35c64-117">If the error continues, restart the computer.</span></span>  
  
4.  <span data-ttu-id="35c64-118">Se o erro persistir, reinstale o Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="35c64-118">If the error recurs, reinstall Visual Basic.</span></span>  
  
5.  <span data-ttu-id="35c64-119">Se o erro persistir após a reinstalação, notifique o Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="35c64-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="35c64-120">Para verificar atributos de arquivo no Explorador de Arquivos</span><span class="sxs-lookup"><span data-stu-id="35c64-120">To check file attributes in File Explorer</span></span>  
  
1.  <span data-ttu-id="35c64-121">Abra a pasta que lhe interessa.</span><span class="sxs-lookup"><span data-stu-id="35c64-121">Open the folder you are interested in.</span></span>  
  
2.  <span data-ttu-id="35c64-122">Clique o **exibições** ícone e escolha **detalhes**.</span><span class="sxs-lookup"><span data-stu-id="35c64-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3.  <span data-ttu-id="35c64-123">Clique com botão direito no cabeçalho da coluna e escolha **atributos** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="35c64-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="35c64-124">Para alterar os atributos de um arquivo ou pasta</span><span class="sxs-lookup"><span data-stu-id="35c64-124">To change the attributes of a file or folder</span></span>  
  
1.  <span data-ttu-id="35c64-125">Em **Explorador de arquivos**, com o botão direito no arquivo ou pasta e escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="35c64-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="35c64-126">No **atributos** seção o **geral** guia, desmarque o **somente leitura** caixa.</span><span class="sxs-lookup"><span data-stu-id="35c64-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3.  <span data-ttu-id="35c64-127">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="35c64-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35c64-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35c64-128">See Also</span></span>  
 [<span data-ttu-id="35c64-129">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="35c64-129">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
