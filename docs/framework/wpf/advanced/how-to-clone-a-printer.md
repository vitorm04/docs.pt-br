---
title: 'Como: Clonar uma impressora'
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
ms.openlocfilehash: f654c9f1431a0ab8aa4df568b405dabf881bb1bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104085"
---
# <a name="how-to-clone-a-printer"></a><span data-ttu-id="f7f5c-102">Como: Clonar uma impressora</span><span class="sxs-lookup"><span data-stu-id="f7f5c-102">How to: Clone a Printer</span></span>
<span data-ttu-id="f7f5c-103">A maioria das empresas comprará várias impressoras do mesmo modelo em algum momento.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-103">Most businesses will, at some point, buy multiple printers of the same model.</span></span> <span data-ttu-id="f7f5c-104">Normalmente, elas são instaladas com configurações praticamente idênticas.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-104">Typically, these are all installed with virtually identical configuration settings.</span></span> <span data-ttu-id="f7f5c-105">Instalar cada impressora pode ser um processo demorado e sujeito a erros.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-105">Installing each printer can be time-consuming and error prone.</span></span> <span data-ttu-id="f7f5c-106">O <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> namespace e o <xref:System.Printing.PrintServer.InstallPrintQueue%2A> classe que são expostos com o Microsoft .NET Framework possibilita a instalação instantânea de qualquer número de filas de impressão adicionais que são clonadas de uma fila de impressa existente.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-106">The <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> namespace and the <xref:System.Printing.PrintServer.InstallPrintQueue%2A> class that are exposed with Microsoft .NET Framework makes it possible to instantly install any number of additional print queues that are cloned from an existing print queue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7f5c-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7f5c-107">Example</span></span>  
 <span data-ttu-id="f7f5c-108">No exemplo abaixo, uma segunda fila de impressão é clonada de uma fila de impressão existente.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-108">In the example below, a second print queue is cloned from an existing print queue.</span></span> <span data-ttu-id="f7f5c-109">A segunda difere da primeira somente no nome, localização, porta e status compartilhado.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-109">The second differs from the first only in its name, location, port, and shared status.</span></span> <span data-ttu-id="f7f5c-110">As principais etapas para fazer isso são as seguintes.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-110">The major steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="f7f5c-111">Criar um <xref:System.Printing.PrintQueue> objeto para a impressora existente que está prestes a ser clonada.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-111">Create a <xref:System.Printing.PrintQueue> object for the existing printer that is going to be cloned.</span></span>  
  
2.  <span data-ttu-id="f7f5c-112">Criar uma <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> do <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> da <xref:System.Printing.PrintQueue>.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-112">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> of the <xref:System.Printing.PrintQueue>.</span></span> <span data-ttu-id="f7f5c-113">O <xref:System.Collections.DictionaryEntry.Value%2A> propriedade de cada entrada neste dicionário é um objeto de um tipo derivado de <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-113">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span> <span data-ttu-id="f7f5c-114">Há duas maneiras de definir o valor de uma entrada neste dicionário.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-114">There are two ways to set the value of an entry in this dictionary.</span></span>  
  
    -   <span data-ttu-id="f7f5c-115">Usar o dicionário **remova** e <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> métodos para remover a entrada e, em seguida, adicioná-la novamente com o valor desejado.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-115">Use the dictionary's **Remove** and <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> methods to remove the entry and then re-add it with the desired value.</span></span>  
  
    -   <span data-ttu-id="f7f5c-116">Usar o dicionário <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> método.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-116">Use the dictionary's <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> method.</span></span>  
  
     <span data-ttu-id="f7f5c-117">O exemplo abaixo ilustra ambas as direções.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-117">The example below illustrates both ways.</span></span>  
  
3.  <span data-ttu-id="f7f5c-118">Criar uma <xref:System.Printing.IndexedProperties.PrintBooleanProperty> do objeto e defina sua <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> para "IsShared" e seu <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> para `true`.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-118">Create a <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "IsShared" and its <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="f7f5c-119">Use o <xref:System.Printing.IndexedProperties.PrintBooleanProperty> objeto como sendo o valor da <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>da entrada "IsShared".</span><span class="sxs-lookup"><span data-stu-id="f7f5c-119">Use the <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" entry.</span></span>  
  
5.  <span data-ttu-id="f7f5c-120">Criar uma <xref:System.Printing.IndexedProperties.PrintStringProperty> do objeto e defina sua <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> para "ShareName" e seu <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> com um número apropriado <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-120">Create a <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "ShareName" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
6.  <span data-ttu-id="f7f5c-121">Use o <xref:System.Printing.IndexedProperties.PrintStringProperty> objeto como sendo o valor da <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>da entrada "ShareName".</span><span class="sxs-lookup"><span data-stu-id="f7f5c-121">Use the <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" entry.</span></span>  
  
7.  <span data-ttu-id="f7f5c-122">Criar outra <xref:System.Printing.IndexedProperties.PrintStringProperty> do objeto e defina sua <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> para "Location" e seu <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> com um número apropriado <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-122">Create another <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "Location" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
8.  <span data-ttu-id="f7f5c-123">Use a segunda <xref:System.Printing.IndexedProperties.PrintStringProperty> objeto como sendo o valor da <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>da entrada "Location".</span><span class="sxs-lookup"><span data-stu-id="f7f5c-123">Use the second <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Location" entry.</span></span>  
  
9. <span data-ttu-id="f7f5c-124">Criar uma matriz de <xref:System.String>s.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-124">Create an array of <xref:System.String>s.</span></span> <span data-ttu-id="f7f5c-125">Cada item é o nome de uma porta no servidor.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-125">Each item is the name of a port on the server.</span></span>  
  
10. <span data-ttu-id="f7f5c-126">Use <xref:System.Printing.PrintServer.InstallPrintQueue%2A> para instalar a nova impressora com os novos valores.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-126">Use <xref:System.Printing.PrintServer.InstallPrintQueue%2A> to install the new printer with the new values.</span></span>  
  
 <span data-ttu-id="f7f5c-127">Veja um exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-127">An example is below.</span></span>  
  
 [!code-csharp[ClonePrinter#ClonePrinter](~/samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a><span data-ttu-id="f7f5c-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7f5c-128">See also</span></span>

- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [<span data-ttu-id="f7f5c-129">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="f7f5c-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="f7f5c-130">Visão geral da impressão</span><span class="sxs-lookup"><span data-stu-id="f7f5c-130">Printing Overview</span></span>](printing-overview.md)
