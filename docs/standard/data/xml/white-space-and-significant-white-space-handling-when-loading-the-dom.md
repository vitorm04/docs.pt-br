---
title: "Espaço em branco e tratamento processamento de espaço em branco para carregar os DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 82401a18132801f9aa5368832b96be3cb67a8642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Espaço em branco e tratamento processamento de espaço em branco para carregar os DOM
Ao carregar o documento, você pode definir a opção para preservar espaço em branco e criar **XmlWhitespace** nós na árvore do documento. Para criar nós de espaços em branco, defina o **PreserveWhitespace** propriedade como true. Se a propriedade é definida como **false**, que é o padrão, nós de espaço em branco não são criados. Nós de espaços em branco são sempre preservados, e **XmlSignificantWhitespace** nós sempre são criados na memória para representar esses dados, independentemente da configuração do **PreserveWhitespace** sinalizador.  
  
 Se o documento é carregado de um leitor, em seguida, a configuração do **PreserveWhitespace** sinalizador de propriedade no **XmlDocument** classe afeta a criação de **XmlWhitespace** nós somente quando o **WhitespaceHandling** propriedade o **XmlTextReader** não está definido como **eram**. É o valor de **WhitespaceHandling** propriedade do leitor que tem precedência sobre a configuração do sinalizador no **XmlDocument**. Para obter mais informações sobre **XmlSignificantWhitespace**, consulte <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
