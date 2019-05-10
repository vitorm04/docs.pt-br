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
ms.openlocfilehash: e6af8d6410c4e383990bdaa27f97cc698be71719
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649197"
---
# <a name="how-to-clone-a-printer"></a>Como: Clonar uma impressora
A maioria das empresas comprará várias impressoras do mesmo modelo em algum momento. Normalmente, elas são instaladas com configurações praticamente idênticas. Instalar cada impressora pode ser um processo demorado e sujeito a erros. O <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> namespace e o <xref:System.Printing.PrintServer.InstallPrintQueue%2A> classe que são expostos com o Microsoft .NET Framework possibilita a instalação instantânea de qualquer número de filas de impressão adicionais que são clonadas de uma fila de impressa existente.  
  
## <a name="example"></a>Exemplo  
 No exemplo abaixo, uma segunda fila de impressão é clonada de uma fila de impressão existente. A segunda difere da primeira somente no nome, localização, porta e status compartilhado. As principais etapas para fazer isso são as seguintes.  
  
1. Criar um <xref:System.Printing.PrintQueue> objeto para a impressora existente que está prestes a ser clonada.  
  
2. Criar uma <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> do <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> da <xref:System.Printing.PrintQueue>. O <xref:System.Collections.DictionaryEntry.Value%2A> propriedade de cada entrada neste dicionário é um objeto de um tipo derivado de <xref:System.Printing.IndexedProperties.PrintProperty>. Há duas maneiras de definir o valor de uma entrada neste dicionário.  
  
    - Usar o dicionário **remova** e <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> métodos para remover a entrada e, em seguida, adicioná-la novamente com o valor desejado.  
  
    - Usar o dicionário <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> método.  
  
     O exemplo abaixo ilustra ambas as direções.  
  
3. Criar uma <xref:System.Printing.IndexedProperties.PrintBooleanProperty> do objeto e defina sua <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> para "IsShared" e seu <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> para `true`.  
  
4. Use o <xref:System.Printing.IndexedProperties.PrintBooleanProperty> objeto como sendo o valor da <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>da entrada "IsShared".  
  
5. Criar uma <xref:System.Printing.IndexedProperties.PrintStringProperty> do objeto e defina sua <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> para "ShareName" e seu <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> com um número apropriado <xref:System.String>.  
  
6. Use o <xref:System.Printing.IndexedProperties.PrintStringProperty> objeto como sendo o valor da <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>da entrada "ShareName".  
  
7. Criar outra <xref:System.Printing.IndexedProperties.PrintStringProperty> do objeto e defina sua <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> para "Location" e seu <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> com um número apropriado <xref:System.String>.  
  
8. Use a segunda <xref:System.Printing.IndexedProperties.PrintStringProperty> objeto como sendo o valor da <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>da entrada "Location".  
  
9. Criar uma matriz de <xref:System.String>s. Cada item é o nome de uma porta no servidor.  
  
10. Use <xref:System.Printing.PrintServer.InstallPrintQueue%2A> para instalar a nova impressora com os novos valores.  
  
 Veja um exemplo abaixo.  
  
 [!code-csharp[ClonePrinter#ClonePrinter](~/samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [Documentos no WPF](documents-in-wpf.md)
- [Visão Geral da Impressão](printing-overview.md)
