---
title: Espaço em branco e tratamento processamento de espaço em branco para carregar os DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d9bbb14320b84a6d417c5c28026b169092de219
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47230769"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Espaço em branco e tratamento processamento de espaço em branco para carregar os DOM
Ao carregar o documento, você pode definir a opção de preservar espaço em branco e criar nós de **XmlWhitespace** na árvore do documento. Para criar nós de espaço em branco, defina a propriedade **PreserveWhitespace** como verdadeiro. Se a propriedade for definida como **falso**, que é o padrão, os nós de espaço em branco não serão criados. Os nós significativos de espaços em branco são preservados sempre, e os nós **XmlSignificantWhitespace** sempre são criados na memória para representar esses dados, independentemente da configuração de sinalizador de **PreserveWhitespace**.  
  
 Se o documento for carregado de um leitor, a configuração da propriedade do sinalizador **PreserveWhitespace** na classe **XmlDocument** afetará a criação de nós **XmlWhitespace** somente quando a propriedade **WhitespaceHandling** em **XmlTextReader** não for definida como **WhitespaceHandling.None**. É o valor da propriedade **WhitespaceHandling** o leitor que tem precedência sobre a configuração de aquele sinalizador no **XmlDocument**. Para saber mais sobre **XmlSignificantWhitespace**, veja <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>Consulte também

- [DOM (Modelo de Objeto do Documento) de XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
