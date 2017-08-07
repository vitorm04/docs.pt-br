---
title: "Como converter RTF em texto sem formatação (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], converting from RTF
ms.assetid: 3b386a87-899d-4d98-bc82-a980526ddaac
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e4c7b48467f3b260526c604fa3a36fc5d80374e
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-rtf-to-plain-text-c-programming-guide"></a>Como converter RTF em texto sem formatação (Guia de Programação em C#)
O Formato Rich Text (RTF) é um formato de documento desenvolvido pela Microsoft no final dos anos 1980 para habilitar a troca de documentos entre sistemas operacionais. O Microsoft Word e o WordPad podem ler e gravar documentos RTF. No .NET Framework, é possível usar o controle <xref:System.Windows.Forms.RichTextBox> para criar um processador de texto que dá suporte ao RTF e habilite um usuário a aplicar formatação ao texto da forma WYSIWIG.  
  
 Também é possível utilizar o controle <xref:System.Windows.Forms.RichTextBox> para remover programaticamente os códigos de formatação RTF de um documento e convertê-lo em texto sem formatação. Não é necessário inserir o controle em um formulário do Windows para executar esse tipo de operação.  
  
### <a name="to-use-the-richtextbox-control-in-a-project"></a>Para usar o controle RichTextBox em um projeto  
  
1.  Adicionar uma referência para System.Windows.Forms.dll.  
  
2.  Adicione uma diretiva de uso para o namespace `System.Windows.Forms` (opcional).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir converte um arquivo RTF de exemplo para texto sem formatação. O arquivo contém a formatação RTF (como informações de fonte), quatro caracteres Unicode e quatro caracteres ASCII estendidos. O código de exemplo abre o arquivo, passa seu conteúdo para um <xref:System.Windows.Forms.RichTextBox> como RTF, recupera o conteúdo como texto, exibe o texto em um <xref:System.Windows.Forms.MessageBox> e gera um arquivo em formato UTF-8 com o texto.  
  
 O `MessageBox` e o arquivo de saída contêm o seguinte texto:  
  
```  
The Greek word for "psyche" is spelled ψυχή. The Greek letters are encoded in Unicode.  
These characters are from the extended ASCII character set (Windows code page 1252):  âäӑå  
```  
  
 [!code-cs[csProgGuideStrings#33](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-rtf-to-plain-text_1.cs)]  
  
 Caracteres RTF são codificados em oito bits. No entanto, os usuários podem especificar caracteres Unicode, além de caracteres ASCII de páginas de código especificadas. Já que a propriedade <xref:System.Windows.Forms.RichTextBox.Text%2A?displayProperty=fullName> é do tipo [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md), os caracteres são codificados como Unicode UTF-16. Quaisquer caracteres ASCII estendidos e Unicode do documento RTF de origem serão codificados corretamente na saída de texto.  
  
 Ao usar o método <xref:System.IO.File.WriteAllText%2A?displayProperty=fullName> para gravar o texto no disco, o texto será codificado como UTF-8 (sem uma marca de ordem de byte).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.RichTextBox?displayProperty=fullName>   
 [Cadeias de Caracteres](../../../csharp/programming-guide/strings/index.md)

