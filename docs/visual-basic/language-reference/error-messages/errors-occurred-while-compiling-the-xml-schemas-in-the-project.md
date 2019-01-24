---
title: Ocorreram erros na compilação dos esquemas XML no projeto
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 17886ececbd418ae60d6321c7a6278a1e982b9af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611274"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="7506c-102">Ocorreram erros na compilação dos esquemas XML no projeto</span><span class="sxs-lookup"><span data-stu-id="7506c-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="7506c-103">Ocorreram erros ao compilar os esquemas XML no projeto.</span><span class="sxs-lookup"><span data-stu-id="7506c-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="7506c-104">Por isso, o XML IntelliSense não está disponível.</span><span class="sxs-lookup"><span data-stu-id="7506c-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="7506c-105">Há um erro em um esquema de definição de esquema XML (XSD) incluído no projeto.</span><span class="sxs-lookup"><span data-stu-id="7506c-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="7506c-106">Esse erro ocorre quando você adiciona um arquivo de esquema (. xsd) de XSD que está em conflito com o esquema XSD existente definido para o projeto.</span><span class="sxs-lookup"><span data-stu-id="7506c-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="7506c-107">**ID do erro:** BC36810</span><span class="sxs-lookup"><span data-stu-id="7506c-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7506c-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7506c-108">To correct this error</span></span>  
  
-   <span data-ttu-id="7506c-109">Clique duas vezes no aviso na **lista de erros** janela.</span><span class="sxs-lookup"><span data-stu-id="7506c-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="7506c-110">Visual Basic levará você até o local no arquivo XSD que é a origem do aviso.</span><span class="sxs-lookup"><span data-stu-id="7506c-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="7506c-111">Corrija o erro no esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="7506c-111">Correct the error in the XSD schema.</span></span>  
  
-   <span data-ttu-id="7506c-112">Garanta que todos os arquivos de esquema (. xsd) de XSD são incluídos no projeto.</span><span class="sxs-lookup"><span data-stu-id="7506c-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="7506c-113">Você talvez precise clicar **Show All Files** na **projeto** menu para ver seu. xsd de arquivos no **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="7506c-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="7506c-114">Um arquivo. xsd com o botão direito e, em seguida, clique em **Include In Project** para incluir o arquivo em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7506c-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
-   <span data-ttu-id="7506c-115">Se você estiver usando o Assistente de XML para esquema, esse erro pode ocorrer se você inferir esquemas mais de uma vez da mesma fonte.</span><span class="sxs-lookup"><span data-stu-id="7506c-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="7506c-116">Nesse caso, você pode remover os arquivos de esquema XSD existentes do projeto, adicione um novo XML ao modelo de item de esquema e, em seguida, forneça o XML para o Assistente de esquema com todas as fontes XML aplicáveis para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7506c-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
-   <span data-ttu-id="7506c-117">Se nenhum erro for identificado no esquema XSD, o compilador XML não pode ter informações suficientes para fornecer uma mensagem de erro detalhada.</span><span class="sxs-lookup"><span data-stu-id="7506c-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="7506c-118">Você poderá obter informações mais detalhadas de erro se você garantir que os namespaces XML para os arquivos. xsd incluídos em seu projeto correspondam os namespaces XML identificados para o esquema XML definido no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7506c-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7506c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7506c-119">See also</span></span>
- [<span data-ttu-id="7506c-120">Janela Lista de Erros</span><span class="sxs-lookup"><span data-stu-id="7506c-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)
- [<span data-ttu-id="7506c-121">XML</span><span class="sxs-lookup"><span data-stu-id="7506c-121">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
