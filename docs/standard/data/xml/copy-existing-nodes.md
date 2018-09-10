---
title: Copiar nós existentes
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eda5c9b4851b29c0a76e45414d7c47ba52252455
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252864"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="6c20c-102">Copiar nós existentes</span><span class="sxs-lookup"><span data-stu-id="6c20c-102">Copy Existing Nodes</span></span>
<span data-ttu-id="6c20c-103">Há vários métodos e propriedades no modelo de objeto (DOM) de documento XML você pode usar para selecionar um nó, como **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span><span class="sxs-lookup"><span data-stu-id="6c20c-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="6c20c-104">Uma vez que o nó é selecionado, você pode inseri-lo na árvore usando um dos métodos de inserção que funcionam para esse tipo de nó específico.</span><span class="sxs-lookup"><span data-stu-id="6c20c-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="6c20c-105">A única limitação para inserir um nó na árvore é que o documento ainda deve ser bem formado depois que o nó é inserido.</span><span class="sxs-lookup"><span data-stu-id="6c20c-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="6c20c-106">Quando um nó existente é inserido na árvore DOM, é removido da sua posição original e adicionado à sua posição de destino.</span><span class="sxs-lookup"><span data-stu-id="6c20c-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c20c-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c20c-107">See also</span></span>

- [<span data-ttu-id="6c20c-108">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="6c20c-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
