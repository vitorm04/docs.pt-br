---
title: Ocorreu um erro inesperado porque não foi possível adquirir um recurso do sistema operacional obrigatório para a inicialização de instância única
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 9aa7ba0babe0a89942e320a76e07c05162b31700
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313600"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="257ab-102">Ocorreu um erro inesperado porque não foi possível adquirir um recurso do sistema operacional obrigatório para a inicialização de instância única</span><span class="sxs-lookup"><span data-stu-id="257ab-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="257ab-103">O aplicativo não pôde adquirir um recurso do sistema operacional necessário.</span><span class="sxs-lookup"><span data-stu-id="257ab-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="257ab-104">Algumas das causas possíveis para esse problema são:</span><span class="sxs-lookup"><span data-stu-id="257ab-104">Some of the possible causes for this problem are:</span></span>  
  
-   <span data-ttu-id="257ab-105">O aplicativo não possui permissão para criar objetos nomeados do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="257ab-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
-   <span data-ttu-id="257ab-106">O Common Language Runtime não tem permissões para criar arquivos de memória mapeada.</span><span class="sxs-lookup"><span data-stu-id="257ab-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
-   <span data-ttu-id="257ab-107">O aplicativo precisa acessar um objeto do sistema operacional, mas outro processo o está usando.</span><span class="sxs-lookup"><span data-stu-id="257ab-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="257ab-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="257ab-108">To correct this error</span></span>  
  
1. <span data-ttu-id="257ab-109">Verifique se o aplicativo possui permissões suficientes para criar objetos nomeados do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="257ab-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2. <span data-ttu-id="257ab-110">Verifique se o Common Language Runtime possui permissões suficientes para criar arquivos de memória mapeada.</span><span class="sxs-lookup"><span data-stu-id="257ab-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3. <span data-ttu-id="257ab-111">Reinicie o computador para limpar qualquer processo que possa estar usando os recursos necessários para se conectar ao aplicativo da instância original.</span><span class="sxs-lookup"><span data-stu-id="257ab-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4. <span data-ttu-id="257ab-112">Observe as circunstâncias sob as quais ocorreu o erro e chame o Microsoft Product Support Services</span><span class="sxs-lookup"><span data-stu-id="257ab-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="257ab-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="257ab-113">See also</span></span>

- [<span data-ttu-id="257ab-114">Página de Aplicativo, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="257ab-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="257ab-115">Noções básicas do depurador</span><span class="sxs-lookup"><span data-stu-id="257ab-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
- [<span data-ttu-id="257ab-116">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="257ab-116">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
