---
title: Verificação de nome de elemento XML e de atributo para criar novos nós
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de11c190310dec90bd23d044f77d0c38e3a34fcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568843"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="a213a-102">Verificação de nome de elemento XML e de atributo para criar novos nós</span><span class="sxs-lookup"><span data-stu-id="a213a-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="a213a-103">O modelo de objeto de documento XML (DOM) verifica a validade de nomes ao criar novos nós ou nós de atributo do elemento.</span><span class="sxs-lookup"><span data-stu-id="a213a-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="a213a-104">Se os nomes contenham caracteres inválidos, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="a213a-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="a213a-105">Para garantir que os nomes sejam válidos e codificados corretamente, você precisa usar a classe **XmlConvert** para codificar o nome e descodificá-lo de volta para o nível de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a213a-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="a213a-106">**XmlWriter** tem métodos que realizam trabalho adicional para garantir que XML corretamente formado seja gerado.</span><span class="sxs-lookup"><span data-stu-id="a213a-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a213a-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a213a-107">See Also</span></span>  
 [<span data-ttu-id="a213a-108">DOM (Modelo de Objeto do Documento) de XML</span><span class="sxs-lookup"><span data-stu-id="a213a-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
