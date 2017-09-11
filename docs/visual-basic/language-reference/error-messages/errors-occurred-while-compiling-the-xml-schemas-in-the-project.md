---
title: Ocorreram erros ao compilar os esquemas XML no projeto | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36810
- vbc36810
dev_langs:
- VB
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: 11
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
ms.openlocfilehash: 7e6a835f84f2e37f4f583bc16c24cf9bb28cc92a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="8582a-102">Ocorreram erros na compilação dos esquemas XML no projeto</span><span class="sxs-lookup"><span data-stu-id="8582a-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="8582a-103">Ocorreram erros ao compilar os esquemas XML no projeto.</span><span class="sxs-lookup"><span data-stu-id="8582a-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="8582a-104">Por isso, o XML IntelliSense não está disponível.</span><span class="sxs-lookup"><span data-stu-id="8582a-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="8582a-105">Há um erro em um esquema de definição de esquema XML (XSD) incluído no projeto.</span><span class="sxs-lookup"><span data-stu-id="8582a-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="8582a-106">Esse erro ocorre quando você adiciona um arquivo de esquema (. xsd) de XSD que está em conflito com o esquema XSD existente definido para o projeto.</span><span class="sxs-lookup"><span data-stu-id="8582a-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="8582a-107">**ID do erro:** BC36810</span><span class="sxs-lookup"><span data-stu-id="8582a-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8582a-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8582a-108">To correct this error</span></span>  
  
-   <span data-ttu-id="8582a-109">Clique duas vezes no aviso no **lista de erros** janela.</span><span class="sxs-lookup"><span data-stu-id="8582a-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="8582a-110">Visual Basic levará você para o local no arquivo XSD que é a origem do aviso.</span><span class="sxs-lookup"><span data-stu-id="8582a-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="8582a-111">Corrija o erro no esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="8582a-111">Correct the error in the XSD schema.</span></span>  
  
-   <span data-ttu-id="8582a-112">Garantir que todos os arquivos de esquema (. xsd) de XSD são incluídos no projeto.</span><span class="sxs-lookup"><span data-stu-id="8582a-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="8582a-113">Talvez você precise clicar em **Show All Files** no **projeto** arquivos para ver seu. xsd em **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="8582a-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="8582a-114">Clique em um arquivo. xsd e, em seguida, clique em **incluir no projeto** para incluir o arquivo no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="8582a-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
-   <span data-ttu-id="8582a-115">Se você estiver usando o Assistente de XML para esquema, esse erro pode ocorrer se você inferir esquemas mais de uma vez da mesma fonte.</span><span class="sxs-lookup"><span data-stu-id="8582a-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="8582a-116">Nesse caso, você pode remover os arquivos de esquema XSD existentes do projeto, adicione um novo XML ao modelo de item de esquema e forneça o XML para Assistente de esquema com todas as fontes XML aplicáveis para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="8582a-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
-   <span data-ttu-id="8582a-117">Se nenhum erro for identificado no seu esquema XSD, o compilador XML pode não ter informações suficientes para fornecer uma mensagem de erro detalhada.</span><span class="sxs-lookup"><span data-stu-id="8582a-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="8582a-118">Você poderá obter informações mais detalhadas de erro se você garantir que namespaces XML para os arquivos. xsd incluídos em seu projeto correspondam a namespaces XML identificados para o esquema XML definido no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8582a-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8582a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8582a-119">See Also</span></span>  
 <span data-ttu-id="8582a-120">[Janela lista de erros](https://docs.microsoft.com/visualstudio/ide/reference/error-list-window) </span><span class="sxs-lookup"><span data-stu-id="8582a-120">[Error List Window](https://docs.microsoft.com/visualstudio/ide/reference/error-list-window) </span></span>  
<span data-ttu-id="8582a-121"> [XML IntelliSense no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md) </span><span class="sxs-lookup"><span data-stu-id="8582a-121"> [XML IntelliSense in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md) </span></span>  
<span data-ttu-id="8582a-122"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)</span><span class="sxs-lookup"><span data-stu-id="8582a-122"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)</span></span>
