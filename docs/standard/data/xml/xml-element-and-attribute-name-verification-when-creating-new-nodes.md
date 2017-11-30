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
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="f182f-102">Verificação de nome de elemento XML e de atributo para criar novos nós</span><span class="sxs-lookup"><span data-stu-id="f182f-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="f182f-103">O modelo de objeto de documento XML (DOM) verifica a validade de nomes ao criar novos nós ou nós de atributo do elemento.</span><span class="sxs-lookup"><span data-stu-id="f182f-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="f182f-104">Se os nomes contenham caracteres inválidos, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="f182f-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="f182f-105">Para garantir que os nomes são válidas e estão codificados corretamente, você precisa usar o **XmlConvert** classe para codificar o nome e decodificá-la novamente no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f182f-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="f182f-106">O **XmlWriter** tem métodos que fazem o trabalho adicional para garantir que é gerado XML bem formado.</span><span class="sxs-lookup"><span data-stu-id="f182f-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f182f-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f182f-107">See Also</span></span>  
 [<span data-ttu-id="f182f-108">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="f182f-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
