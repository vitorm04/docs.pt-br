---
title: Como usar caracteres especiais em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: d60f9e94fd93c95e573bb52847c717821abdd9a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-special-characters-in-xaml"></a>Como usar caracteres especiais em XAML
Arquivos de marcação que são criados no [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] são salvas automaticamente no [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] formato de arquivo UTF-8, o que significa que a maioria dos caracteres especiais, como marcas de ênfase são codificados corretamente. No entanto, há um conjunto de caracteres especiais comumente usados que são tratados de maneira diferente. Esses caracteres especiais seguem o [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] padrão de codificação.  
  
 A tabela a seguir mostra a sintaxe para a codificação deste conjunto de caracteres especiais:  
  
|Caractere|Sintaxe|Descrição|  
|---------------|------------|-----------------|  
|<|`<`|Menor que o símbolo.|  
|>|`>`|Sinal de maior que.|  
|&|`&`|Símbolo de e comercial.|  
|"|`"`|Símbolo de aspas duplas.|  
  
> [!NOTE]
>  Se você criar um arquivo de marcação usando um texto de editor, como [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] bloco de notas, você deve salvar o arquivo no [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] codificado de formato de arquivo UTF-8 para preservar os caracteres especiais.  
  
 O exemplo a seguir mostra como você pode usar caracteres especiais em texto quando criar a marcação.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
