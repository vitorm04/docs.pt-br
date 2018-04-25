---
title: Objetos de extensão XSLT
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
caps.latest.revision: 3
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 72b1605c6bc5a0f3cbc4417d043ab21bf0bb787e
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="xslt-extension-objects"></a>Objetos de extensão XSLT
Os objetos de extensão são usados para estender a funcionalidade de folhas de estilos. Os objetos de extensão são mantidos pela classe de <xref:System.Xml.Xsl.XsltArgumentList> .  
  
 Os seguintes são vantagens de usar um objeto de extensão em vez do script inserido:  
  
-   Fornece a melhor encapsulamento e reutilização de classes.  
  
-   Permite que as folhas de estilos são menores e mais sustentável.  
  
 Os objetos de extensão XSLT são adicionados ao objeto de <xref:System.Xml.Xsl.XsltArgumentList> usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> . Um nome qualificado e URI de namespace são associados com o objeto de extensão no momento.  
  
> [!NOTE]
>  O conjunto de permissões FullTrust é necessário chamar o método de <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> . Para saber mais, confira [Segurança de acesso ao código](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) e [NIB: conjuntos de permissão nomeada](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).  
  
 Os tipos de dados retornados de objetos de extensão é um dos quatro tipos de dados básicos XPath `number`, `string`, `Boolean`, e `node set`.  
  
 Nenhum método que é definido com a palavra-chave `params` , que permite que um número especificado de parâmetros não é passado, não é suportado atualmente pela classe de <xref:System.Xml.Xsl.XslCompiledTransform> . As folhas de estilos XSLT que utilizam qualquer método definido com a palavra-chave `params` não funcionarão corretamente. Para obter detalhes, confira [params](~/docs/csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>Para usar um objeto de extensão XSLT  
  
1.  Crie um objeto de <xref:System.Xml.Xsl.XsltArgumentList> e adicione o objeto de extensão usando o método <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .  
  
2.  Chame o objeto de extensão folha de estilos.  
  
3.  Passe o objeto de <xref:System.Xml.Xsl.XsltArgumentList> para o método de <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .  
  
## <a name="see-also"></a>Consulte também  
 [Transformações XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [Considerações de segurança de XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md)
