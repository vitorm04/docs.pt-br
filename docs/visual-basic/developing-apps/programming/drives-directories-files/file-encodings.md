---
title: Codificações de arquivo
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: 52770187568d0ba0f54ec36ee2c3d754a9b4d9a8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348886"
---
# <a name="file-encodings-visual-basic"></a>Codificações de arquivo (Visual Basic)

As codificações de arquivo, também conhecidas como codificações de caracteres, especificam como representar caracteres no processamento de texto. Uma codificação pode ser preferível em relação a outra em termos de quais caracteres de idioma podem ou não ser manipulados, embora o Unicode geralmente seja o ideal.

Durante a leitura ou gravação em arquivos, combinar incorretamente as codificações de arquivo pode resultar em exceções ou resultados incorretos.

## <a name="types-of-encodings"></a>Tipos de Codificações

O Unicode é a codificação preferencial ao trabalhar com arquivos. O Unicode é um padrão de codificação de caracteres global que usa valores de código de 16 bits para representar todos os caracteres utilizados na computação moderna, incluindo símbolos técnicos e caracteres especiais usados em publicações.

Os padrões de codificação de caracteres anteriores consistiam em conjuntos de caracteres tradicionais, como o conjunto de caracteres ANSI do Windows que usa valores de código de 8 bits ou combinações de valores de 8 bits, a fim de representar os caracteres usados em um idioma ou região geográfica específicos.

## <a name="encoding-class"></a>Classe de Codificação

A classe <xref:System.Text.Encoding> representa uma codificação de caracteres. Esta tabela lista os tipos de codificações disponíveis e descreve cada uma.

|{1&gt;Nome&lt;1}|Descrição|
|---|---|
|<xref:System.Text.ASCIIEncoding>|Representa uma codificação de caracteres ASCII de caracteres Unicode.|
|<xref:System.Text.UnicodeEncoding>|Representa uma codificação de caracteres Unicode UTF-16.|
|<xref:System.Text.UTF32Encoding>|Representa uma codificação de caracteres Unicode UTF-32.|
|<xref:System.Text.UTF7Encoding>|Representa uma codificação de caracteres Unicode UTF-7.|
|<xref:System.Text.UTF8Encoding>|{1&gt;Representa uma codificação de caracteres Unicode UTF-8. &lt;1}|

## <a name="see-also"></a>Consulte também

- [Leitura de arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Gravando em arquivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
