---
title: 'Como: Obter propriedades do objeto do sistema de impressão sem reflexão'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
ms.openlocfilehash: bb906dafd98e75708764b5f0f009900719f6a475
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335193"
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="04a8d-102">Como: Obter propriedades do objeto do sistema de impressão sem reflexão</span><span class="sxs-lookup"><span data-stu-id="04a8d-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="04a8d-103">Usando a reflexão para relacionar as propriedades (e os tipos dessas propriedades) em um objeto pode diminuir o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="04a8d-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="04a8d-104">O <xref:System.Printing.IndexedProperties> namespace fornece um meio para obter essas informações com o uso de reflexão.</span><span class="sxs-lookup"><span data-stu-id="04a8d-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04a8d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="04a8d-105">Example</span></span>  
 <span data-ttu-id="04a8d-106">As etapas para fazer isso são da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="04a8d-106">The steps for doing this are as follows.</span></span>  
  
1. <span data-ttu-id="04a8d-107">Crie uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="04a8d-107">Create an instance of the type.</span></span> <span data-ttu-id="04a8d-108">No exemplo a seguir, o tipo é o <xref:System.Printing.PrintQueue> que é fornecido com o Microsoft .NET Framework, mas código quase idêntico deve funcionar para tipos que derivam de <xref:System.Printing.PrintSystemObject>.</span><span class="sxs-lookup"><span data-stu-id="04a8d-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with Microsoft .NET Framework, but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2. <span data-ttu-id="04a8d-109">Criar uma <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> do tipo de <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span><span class="sxs-lookup"><span data-stu-id="04a8d-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="04a8d-110">O <xref:System.Collections.DictionaryEntry.Value%2A> propriedade de cada entrada neste dicionário é um objeto de um tipo derivado de <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="04a8d-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3. <span data-ttu-id="04a8d-111">Enumere os membros do dicionário.</span><span class="sxs-lookup"><span data-stu-id="04a8d-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="04a8d-112">Para cada um deles, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="04a8d-112">For each of them, do the following.</span></span>  
  
4. <span data-ttu-id="04a8d-113">Cast o valor de cada entrada para <xref:System.Printing.IndexedProperties.PrintProperty> e usá-lo para criar um <xref:System.Printing.IndexedProperties.PrintProperty> objeto.</span><span class="sxs-lookup"><span data-stu-id="04a8d-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5. <span data-ttu-id="04a8d-114">Obter o tipo dos <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> de cada um do <xref:System.Printing.IndexedProperties.PrintProperty> objeto.</span><span class="sxs-lookup"><span data-stu-id="04a8d-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="04a8d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04a8d-115">See also</span></span>

- <xref:System.Printing.IndexedProperties.PrintProperty>
- <xref:System.Printing.PrintSystemObject>
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [<span data-ttu-id="04a8d-116">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="04a8d-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="04a8d-117">Visão geral da impressão</span><span class="sxs-lookup"><span data-stu-id="04a8d-117">Printing Overview</span></span>](printing-overview.md)
