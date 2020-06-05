---
title: O arquivo especificado em FileName não é um arquivo XML válido
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: a84042490935e3e7e5a6de2a802d9effd5b4d3d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358342"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="a093f-102">O arquivo especificado em FileName não é um arquivo XML válido</span><span class="sxs-lookup"><span data-stu-id="a093f-102">File specified in FileName is not a valid XML file</span></span>

<span data-ttu-id="a093f-103">O nome de arquivo que você forneceu não é um arquivo XML válido.</span><span class="sxs-lookup"><span data-stu-id="a093f-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="a093f-104">Para especificar a estrutura permitida e o conteúdo de um documento XML, você pode usar uma definição de tipo de documento (DTD), um esquema do Microsoft XML-Data Reduced (XDR) ou um esquema XSD (XML Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="a093f-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="a093f-105">Os esquemas XSD são a maneira preferida de especificar gramáticas XML no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a093f-105">XSD schemas are the preferred way to specify XML grammars in the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="a093f-106">Em algumas versões anteriores do Visual Studio, o **XML Designer** é o designer para datasets tipados e esquema XML.</span><span class="sxs-lookup"><span data-stu-id="a093f-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="a093f-107">O **Designer de XML** ainda pode ser usado para criar e editar arquivos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="a093f-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="a093f-108">No entanto, no Visual Studio 2012, o designer para criar e editar DataSets tipados é a **Designer de conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="a093f-108">However, in Visual Studio 2012, the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="a093f-109">Para obter mais informações, consulte [criando e editando conjuntos de dados tipados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="a093f-109">For more information, see [Creating and Editing Typed Datasets](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a093f-110">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a093f-110">To correct this error</span></span>

- <span data-ttu-id="a093f-111">Verifique se você está fornecendo o nome de arquivo correto.</span><span class="sxs-lookup"><span data-stu-id="a093f-111">Check that you are supplying the correct file name.</span></span>

- <span data-ttu-id="a093f-112">Verifique se o arquivo especificado contém um XML válido carregando o arquivo XML que você deseja verificar no **XML Designer**.</span><span class="sxs-lookup"><span data-stu-id="a093f-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="a093f-113">No menu **XML** , clique em **validar XML**.</span><span class="sxs-lookup"><span data-stu-id="a093f-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="a093f-114">Os erros são exibidos no **lista de tarefas**.</span><span class="sxs-lookup"><span data-stu-id="a093f-114">Errors are displayed in the **Task List**.</span></span>

- <span data-ttu-id="a093f-115">Se o arquivo XML tiver um esquema XML associado, verifique se os elementos aparecem na estrutura definida e se o conteúdo dos elementos individuais está em conformidade com os tipos de dados declarados especificados no esquema.</span><span class="sxs-lookup"><span data-stu-id="a093f-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>

## <a name="see-also"></a><span data-ttu-id="a093f-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="a093f-116">See also</span></span>

- <xref:System.Xml>
- [<span data-ttu-id="a093f-117">Como: analisar caminhos de arquivo</span><span class="sxs-lookup"><span data-stu-id="a093f-117">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
