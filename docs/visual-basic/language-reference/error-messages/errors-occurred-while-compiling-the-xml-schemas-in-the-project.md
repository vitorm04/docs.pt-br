---
title: Ocorreram erros na compilação dos esquemas XML no projeto
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 0cc565809792c619ca9903f9ef9b029b51a8aa17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588256"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="26026-102">Ocorreram erros na compilação dos esquemas XML no projeto</span><span class="sxs-lookup"><span data-stu-id="26026-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="26026-103">Ocorreram erros ao compilar os esquemas XML no projeto.</span><span class="sxs-lookup"><span data-stu-id="26026-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="26026-104">Por isso, o XML IntelliSense não está disponível.</span><span class="sxs-lookup"><span data-stu-id="26026-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="26026-105">Há um erro em um esquema de definição de esquema XML (XSD) incluído no projeto.</span><span class="sxs-lookup"><span data-stu-id="26026-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="26026-106">Esse erro ocorre quando você adiciona um arquivo de esquema (. xsd) XSD que está em conflito com o esquema XSD existente definido para o projeto.</span><span class="sxs-lookup"><span data-stu-id="26026-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="26026-107">**ID do erro:** BC36810</span><span class="sxs-lookup"><span data-stu-id="26026-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="26026-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="26026-108">To correct this error</span></span>  
  
-   <span data-ttu-id="26026-109">Clique duas vezes no aviso no **lista erros** janela.</span><span class="sxs-lookup"><span data-stu-id="26026-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="26026-110">Visual Basic levará você para o local no arquivo XSD que é a origem do aviso.</span><span class="sxs-lookup"><span data-stu-id="26026-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="26026-111">Corrija o erro no esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="26026-111">Correct the error in the XSD schema.</span></span>  
  
-   <span data-ttu-id="26026-112">Garantir que todos os arquivos de esquema (. xsd) XSD são incluídos no projeto.</span><span class="sxs-lookup"><span data-stu-id="26026-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="26026-113">Talvez você precise clicar em **Mostrar todos os arquivos** no **projeto** para ver seu. xsd arquivos em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="26026-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="26026-114">Clique em um arquivo. xsd e, em seguida, clique em **incluir no projeto** para incluir o arquivo no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="26026-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
-   <span data-ttu-id="26026-115">Se você estiver usando o Assistente de esquema XML, esse erro pode ocorrer se inferir esquemas mais de uma vez da mesma fonte.</span><span class="sxs-lookup"><span data-stu-id="26026-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="26026-116">Nesse caso, você pode remover os arquivos existentes do esquema XSD do projeto, adicione um novo XML para o modelo de item de esquema e, em seguida, forneça o XML ao Assistente de esquema com todas as fontes de XML aplicável para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="26026-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
-   <span data-ttu-id="26026-117">Se nenhum erro for identificado no seu esquema XSD, o compilador XML pode não ter informações suficientes para fornecer uma mensagem de erro detalhada.</span><span class="sxs-lookup"><span data-stu-id="26026-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="26026-118">Você poderá obter informações mais detalhadas de erro se você garantir que os namespaces XML para os arquivos. xsd incluídos em seu projeto correspondam a namespaces XML identificados para o esquema XML definido no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26026-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26026-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26026-119">See Also</span></span>  
 [<span data-ttu-id="26026-120">Janela Lista de Erros</span><span class="sxs-lookup"><span data-stu-id="26026-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)  
 [<span data-ttu-id="26026-121">XML</span><span class="sxs-lookup"><span data-stu-id="26026-121">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
