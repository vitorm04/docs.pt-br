---
title: 'Como: Usar caracteres especiais em XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 61ee38319b2f0aa46690fb063f6ffe6612f993ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918442"
---
# <a name="how-to-use-special-characters-in-xaml"></a>Como: Usar caracteres especiais em XAML
Os arquivos de marcação criados no [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] são salvos automaticamente no formato [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] de arquivo UTF-8, o que significa que a maioria dos caracteres especiais, como as marcas de acentuação, são codificados corretamente. No entanto, há um conjunto de caracteres especiais comumente usados que são tratados de forma diferente. Esses caracteres especiais seguem o [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] padrão para codificação.  
  
 A tabela a seguir mostra a sintaxe para codificar esse conjunto de caracteres especiais:  
  
|Caractere|Sintaxe|Descrição|  
|---------------|------------|-----------------|  
|<|`&lt;`|Menor que símbolo.|  
|>|`&gt;`|Sinal de maior que.|  
|&|`&amp;`|Símbolo de e comercial.|  
|"|`&quot;`|Símbolo de aspas duplas.|  
  
> [!NOTE]
> Se você criar um arquivo de marcação usando um editor de texto, como o bloco de notas do Windows, deverá salvar [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] o arquivo no formato de arquivo UTF-8 para preservar os caracteres especiais codificados.  
  
 O exemplo a seguir mostra como você pode usar caracteres especiais no texto ao criar marcação.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
