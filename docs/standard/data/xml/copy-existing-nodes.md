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
# <a name="copy-existing-nodes"></a><span data-ttu-id="5ceeb-102">Copiar nós existentes</span><span class="sxs-lookup"><span data-stu-id="5ceeb-102">Copy Existing Nodes</span></span>
<span data-ttu-id="5ceeb-103">Há vários métodos e propriedades no modelo de objeto (DOM) de documento XML você pode usar para selecionar um nó, como **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span><span class="sxs-lookup"><span data-stu-id="5ceeb-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="5ceeb-104">Uma vez que o nó é selecionado, você pode inseri-lo na árvore usando um dos métodos de inserção que funcionam para esse tipo de nó específico.</span><span class="sxs-lookup"><span data-stu-id="5ceeb-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="5ceeb-105">A única limitação para inserir um nó na árvore é que o documento ainda deve ser bem formado depois que o nó é inserido.</span><span class="sxs-lookup"><span data-stu-id="5ceeb-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="5ceeb-106">Quando um nó existente é inserido na árvore DOM, é removido da sua posição original e adicionado à sua posição de destino.</span><span class="sxs-lookup"><span data-stu-id="5ceeb-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ceeb-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ceeb-107">See Also</span></span>  
 [<span data-ttu-id="5ceeb-108">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="5ceeb-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
