---
title: "Verificação de nome de elemento XML e de atributo para criar novos nós"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c041d5d2830222f3fae09a39f1ea10eb08772388
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>Verificação de nome de elemento XML e de atributo para criar novos nós
O modelo de objeto de documento XML (DOM) verifica a validade de nomes ao criar novos nós ou nós de atributo do elemento. Se os nomes contenham caracteres inválidos, uma exceção é lançada. Para garantir que os nomes são válidas e estão codificados corretamente, você precisa usar o **XmlConvert** classe para codificar o nome e decodificá-la novamente no nível do aplicativo. O **XmlWriter** tem métodos que fazem o trabalho adicional para garantir que é gerado XML bem formado.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
