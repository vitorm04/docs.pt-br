---
title: Ocorreram erros na compilação dos esquemas XML no projeto
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 17c31301e28c757954e72ba103254f038905671f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874356"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="57eee-102">Ocorreram erros na compilação dos esquemas XML no projeto</span><span class="sxs-lookup"><span data-stu-id="57eee-102">Errors occurred while compiling the XML schemas in the project</span></span>

<span data-ttu-id="57eee-103">Ocorreram erros ao compilar os esquemas XML no projeto.</span><span class="sxs-lookup"><span data-stu-id="57eee-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="57eee-104">Por isso, o XML IntelliSense não está disponível.</span><span class="sxs-lookup"><span data-stu-id="57eee-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="57eee-105">Há um erro em um esquema de definição de esquema XML (XSD) incluído no projeto.</span><span class="sxs-lookup"><span data-stu-id="57eee-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="57eee-106">Esse erro ocorre quando você adiciona um arquivo de esquema XSD (. xsd) que está em conflito com o esquema XSD existente definido para o projeto.</span><span class="sxs-lookup"><span data-stu-id="57eee-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="57eee-107">**ID do erro:** BC36810</span><span class="sxs-lookup"><span data-stu-id="57eee-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="57eee-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="57eee-108">To correct this error</span></span>  
  
- <span data-ttu-id="57eee-109">Clique duas vezes no aviso na janela **lista de erros** .</span><span class="sxs-lookup"><span data-stu-id="57eee-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="57eee-110">Visual Basic levará você para o local no arquivo XSD que é a origem do aviso.</span><span class="sxs-lookup"><span data-stu-id="57eee-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="57eee-111">Corrija o erro no esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="57eee-111">Correct the error in the XSD schema.</span></span>  
  
- <span data-ttu-id="57eee-112">Verifique se todos os arquivos de esquema XSD (. xsd) necessários estão incluídos no projeto.</span><span class="sxs-lookup"><span data-stu-id="57eee-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="57eee-113">Talvez seja necessário clicar em **Mostrar todos os arquivos** no menu do **projeto** para ver seus arquivos. xsd no **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="57eee-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="57eee-114">Clique com o botão direito do mouse em um arquivo. xsd e clique em **incluir no projeto** para incluir o arquivo em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="57eee-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
- <span data-ttu-id="57eee-115">Se você estiver usando o assistente de XML para esquema, esse erro poderá ocorrer se você inferir esquemas mais de uma vez da mesma origem.</span><span class="sxs-lookup"><span data-stu-id="57eee-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="57eee-116">Nesse caso, você pode remover os arquivos de esquema XSD existentes do projeto, adicionar um novo XML ao modelo de item de esquema e fornecer o assistente de XML para esquema com todas as fontes XML aplicáveis para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="57eee-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
- <span data-ttu-id="57eee-117">Se nenhum erro for identificado no seu esquema XSD, o compilador XML poderá não ter informações suficientes para fornecer uma mensagem de erro detalhada.</span><span class="sxs-lookup"><span data-stu-id="57eee-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="57eee-118">Você poderá obter informações de erro mais detalhadas se garantir que os namespaces XML para os arquivos. xsd incluídos em seu projeto correspondam aos namespaces XML identificados para o esquema XML definido no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="57eee-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57eee-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="57eee-119">See also</span></span>

- [<span data-ttu-id="57eee-120">Janela de Lista de Erros</span><span class="sxs-lookup"><span data-stu-id="57eee-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)
- [<span data-ttu-id="57eee-121">XML</span><span class="sxs-lookup"><span data-stu-id="57eee-121">XML</span></span>](../../programming-guide/language-features/xml/index.md)
