---
title: "Copiar nós existentes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c026d9f825375d74d53d5cc46969ff0f713bab1c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="copy-existing-nodes"></a>Copiar nós existentes
Há vários métodos e propriedades no modelo de objeto (DOM) de documento XML você pode usar para selecionar um nó, como **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**. Uma vez que o nó é selecionado, você pode inseri-lo na árvore usando um dos métodos de inserção que funcionam para esse tipo de nó específico. A única limitação para inserir um nó na árvore é que o documento ainda deve ser bem formado depois que o nó é inserido. Quando um nó existente é inserido na árvore DOM, é removido da sua posição original e adicionado à sua posição de destino.  
  
## <a name="see-also"></a>Consulte também  
 [DOM (Modelo de Objeto do Documento) de XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
