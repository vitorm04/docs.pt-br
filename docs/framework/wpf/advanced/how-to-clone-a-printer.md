---
title: Como clonar uma impressora
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
ms.openlocfilehash: 8f3a9c3b4d9f4bcbe3a6ffcff9868aa7b19b8f28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544185"
---
# <a name="how-to-clone-a-printer"></a><span data-ttu-id="a6e7a-102">Como clonar uma impressora</span><span class="sxs-lookup"><span data-stu-id="a6e7a-102">How to: Clone a Printer</span></span>
<span data-ttu-id="a6e7a-103">A maioria das empresas comprará várias impressoras do mesmo modelo em algum momento.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-103">Most businesses will, at some point, buy multiple printers of the same model.</span></span> <span data-ttu-id="a6e7a-104">Normalmente, elas são instaladas com configurações praticamente idênticas.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-104">Typically, these are all installed with virtually identical configuration settings.</span></span> <span data-ttu-id="a6e7a-105">Instalar cada impressora pode ser um processo demorado e sujeito a erros.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-105">Installing each printer can be time-consuming and error prone.</span></span> <span data-ttu-id="a6e7a-106">O <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> namespace e o <xref:System.Printing.PrintServer.InstallPrintQueue%2A> classe que são expostos com o Microsoft .NET Framework, é possível instalar instantaneamente qualquer número adicionais de filas de impressão que são clonadas de uma fila de impressão existente.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-106">The <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> namespace and the <xref:System.Printing.PrintServer.InstallPrintQueue%2A> class that are exposed with Microsoft .NET Framework makes it possible to instantly install any number of additional print queues that are cloned from an existing print queue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6e7a-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6e7a-107">Example</span></span>  
 <span data-ttu-id="a6e7a-108">No exemplo abaixo, uma segunda fila de impressão é clonada de uma fila de impressão existente.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-108">In the example below, a second print queue is cloned from an existing print queue.</span></span> <span data-ttu-id="a6e7a-109">A segunda difere da primeira somente no nome, localização, porta e status compartilhado.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-109">The second differs from the first only in its name, location, port, and shared status.</span></span> <span data-ttu-id="a6e7a-110">As principais etapas para fazer isso são as seguintes.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-110">The major steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="a6e7a-111">Criar um <xref:System.Printing.PrintQueue> objeto para a impressora existente a ser clonado.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-111">Create a <xref:System.Printing.PrintQueue> object for the existing printer that is going to be cloned.</span></span>  
  
2.  <span data-ttu-id="a6e7a-112">Criar um <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> do <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> do <xref:System.Printing.PrintQueue>.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-112">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> of the <xref:System.Printing.PrintQueue>.</span></span> <span data-ttu-id="a6e7a-113">O <xref:System.Collections.DictionaryEntry.Value%2A> propriedade de cada entrada neste dicionário é um objeto de um tipo derivado de <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-113">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span> <span data-ttu-id="a6e7a-114">Há duas maneiras de definir o valor de uma entrada neste dicionário.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-114">There are two ways to set the value of an entry in this dictionary.</span></span>  
  
    -   <span data-ttu-id="a6e7a-115">Usar o dicionário **remover** e <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> métodos para remover a entrada e, em seguida, adicioná-la novamente com o valor desejado.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-115">Use the dictionary's **Remove** and <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> methods to remove the entry and then re-add it with the desired value.</span></span>  
  
    -   <span data-ttu-id="a6e7a-116">Usar o dicionário <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-116">Use the dictionary's <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> method.</span></span>  
  
     <span data-ttu-id="a6e7a-117">O exemplo abaixo ilustra ambas as direções.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-117">The example below illustrates both ways.</span></span>  
  
3.  <span data-ttu-id="a6e7a-118">Criar um <xref:System.Printing.IndexedProperties.PrintBooleanProperty> do objeto e defina seu <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> para "IsShared" e seu <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> para `true`.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-118">Create a <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "IsShared" and its <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="a6e7a-119">Use o <xref:System.Printing.IndexedProperties.PrintBooleanProperty> objeto como o valor da <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>da entrada "IsShared".</span><span class="sxs-lookup"><span data-stu-id="a6e7a-119">Use the <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" entry.</span></span>  
  
5.  <span data-ttu-id="a6e7a-120">Criar um <xref:System.Printing.IndexedProperties.PrintStringProperty> do objeto e defina seu <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> para "ShareName" e seu <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> com um número apropriado <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-120">Create a <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "ShareName" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
6.  <span data-ttu-id="a6e7a-121">Use o <xref:System.Printing.IndexedProperties.PrintStringProperty> objeto como o valor da <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>da entrada "ShareName".</span><span class="sxs-lookup"><span data-stu-id="a6e7a-121">Use the <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" entry.</span></span>  
  
7.  <span data-ttu-id="a6e7a-122">Crie outro <xref:System.Printing.IndexedProperties.PrintStringProperty> do objeto e defina seu <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> para "Local" e seu <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> com um número apropriado <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-122">Create another <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "Location" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
8.  <span data-ttu-id="a6e7a-123">Use a segunda <xref:System.Printing.IndexedProperties.PrintStringProperty> objeto como o valor da <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>da entrada de "Local".</span><span class="sxs-lookup"><span data-stu-id="a6e7a-123">Use the second <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Location" entry.</span></span>  
  
9. <span data-ttu-id="a6e7a-124">Crie uma matriz de <xref:System.String>s.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-124">Create an array of <xref:System.String>s.</span></span> <span data-ttu-id="a6e7a-125">Cada item é o nome de uma porta no servidor.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-125">Each item is the name of a port on the server.</span></span>  
  
10. <span data-ttu-id="a6e7a-126">Use <xref:System.Printing.PrintServer.InstallPrintQueue%2A> para instalar a nova impressora com os novos valores.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-126">Use <xref:System.Printing.PrintServer.InstallPrintQueue%2A> to install the new printer with the new values.</span></span>  
  
 <span data-ttu-id="a6e7a-127">Veja um exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="a6e7a-127">An example is below.</span></span>  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a><span data-ttu-id="a6e7a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6e7a-128">See Also</span></span>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="a6e7a-129">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="a6e7a-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="a6e7a-130">Visão Geral da Impressão</span><span class="sxs-lookup"><span data-stu-id="a6e7a-130">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
