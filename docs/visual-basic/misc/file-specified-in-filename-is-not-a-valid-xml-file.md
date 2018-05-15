---
title: Arquivo especificado no nome do arquivo não é um arquivo XML válido
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: 3aecb0c2c87539717656a29f5b48f94fce3c8453
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="619f8-102">Arquivo especificado no nome do arquivo não é um arquivo XML válido</span><span class="sxs-lookup"><span data-stu-id="619f8-102">File specified in FileName is not a valid XML file</span></span>
<span data-ttu-id="619f8-103">O nome do arquivo que você forneceu não é um arquivo XML válido.</span><span class="sxs-lookup"><span data-stu-id="619f8-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="619f8-104">Para especificar a estrutura permitida e o conteúdo de um documento XML, você pode usar uma definição de tipo de documento (DTD), um esquema Microsoft XML-Data Reduced (XDR) ou um esquema de linguagem XSD de definição de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="619f8-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="619f8-105">Esquemas XSD são a melhor maneira de especificar gramáticas XML no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="619f8-105">XSD schemas are the preferred way to specify XML grammars in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="619f8-106">Em algumas versões anteriores do Visual Studio, o **XML Designer** é o designer para datasets tipados e esquema XML.</span><span class="sxs-lookup"><span data-stu-id="619f8-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="619f8-107">O **XML Designer** ainda pode ser usado para criar e editar arquivos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="619f8-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="619f8-108">No entanto, em [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], o designer para criar e editar conjuntos de dados tipados é o **Dataset Designer**.</span><span class="sxs-lookup"><span data-stu-id="619f8-108">However, in [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="619f8-109">Para obter mais informações, consulte [criando e editando conjuntos de dados digitados](/visualstudio/data-tools/creating-and-editing-typed-datasets).</span><span class="sxs-lookup"><span data-stu-id="619f8-109">For more information, see [Creating and Editing Typed Datasets](/visualstudio/data-tools/creating-and-editing-typed-datasets).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="619f8-110">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="619f8-110">To correct this error</span></span>  
  
-   <span data-ttu-id="619f8-111">Verifique se você está fornecendo o nome de arquivo correto.</span><span class="sxs-lookup"><span data-stu-id="619f8-111">Check that you are supplying the correct file name.</span></span>  
  
-   <span data-ttu-id="619f8-112">Verifique se o arquivo especificado contém XML válido ao carregar o arquivo XML que você deseja verificar para o **XML Designer**.</span><span class="sxs-lookup"><span data-stu-id="619f8-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="619f8-113">Do **XML** menu, clique em **Validar XML**.</span><span class="sxs-lookup"><span data-stu-id="619f8-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="619f8-114">Erros são exibidos no **lista de tarefas**.</span><span class="sxs-lookup"><span data-stu-id="619f8-114">Errors are displayed in the **Task List**.</span></span>  
  
-   <span data-ttu-id="619f8-115">Se o arquivo XML tem um esquema XML associado, verifique se os elementos aparecem na estrutura definida e que o conteúdo dos elementos individuais está de acordo com os tipos de dados declarado especificados no esquema.</span><span class="sxs-lookup"><span data-stu-id="619f8-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="619f8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="619f8-116">See Also</span></span>  
 <xref:System.Xml>  
 [<span data-ttu-id="619f8-117">Como analisar demarcadores de arquivo</span><span class="sxs-lookup"><span data-stu-id="619f8-117">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
