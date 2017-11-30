---
title: "Compilação do esquema de XmlSchemaCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 901c3fdc8fdc80cc7c3bf13170646de857a5e009
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xmlschemacollection-schema-compilation"></a>Compilação do esquema de XmlSchemaCollection
O **XmlSchemaCollection** é um cache ou a biblioteca onde os esquemas de linguagem XSD de definição de XML-Data Reduced (XDR) e o esquema XML podem ser armazenados e validados. **XmlSchemaCollection** melhora o desempenho armazenando em cache de esquemas na memória, em vez de acessá-los de um arquivo ou URL.  
  
> [!NOTE]
>  Embora o **XmlSchemaCollection** classe armazena os esquemas XDR e esquemas XML, qualquer método e a propriedade que utiliza ou retorna um **XmlSchema** objeto oferece suporte a esquemas XML apenas.  
  
> [!IMPORTANT]
>  A classe <xref:System.Xml.Schema.XmlSchemaCollection> agora está obsoleta e foi substituída pela classe <xref:System.Xml.Schema.XmlSchemaSet>. Para obter mais informações sobre o <xref:System.Xml.Schema.XmlSchemaSet> , consulte classe [XmlSchemaSet para compilação de esquema](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).  
  
## <a name="add-schemas-to-the-collection"></a>Adicionar à coleção esquemas  
 Os esquemas são carregados para a coleção usando o **adicionar** método **XmlSchemaCollection**, momento em que o esquema está associado um URI de namespace. Para esquemas XML, URI do namespace será normalmente o namespace de destino para o esquema. Para esquemas XDR, o URI de namespace é namespace especificado quando o esquema foi adicionado à coleção.  
  
## <a name="check-for-a-schema-in-the-collection"></a>Verificação para um esquema na coleção  
 Você pode verificar se um esquema está na coleção usando o **contém** método. O **contém** método aceita um **XmlSchema** objeto (para esquemas XML só) ou uma cadeia de caracteres que representa o URI de namespace associado com o esquema (esquemas XDR e de esquemas XML).  
  
## <a name="retrieve-a-schema-from-the-collection"></a>Recuperar um esquema de coleção  
 Você pode recuperar um esquema da coleção usando o **Item** propriedade. O **Item** propriedade usa uma cadeia de caracteres que representa o namespace URI associada ao esquema, normalmente é o namespace de destino e retorna um **XmlSchema** objeto. O **Item** propriedade se aplica somente aos esquemas XML. O valor de retorno é sempre uma referência nula para esquemas XDR porque eles não têm um modelo de objeto disponível.  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>Validar documentos XML usando XmlSchemaCollection  
 Você pode validar um documento de instância XML usando um **XmlSchemaCollection** criando o **XmlSchemaCollection** objeto, adicionando os esquemas na coleção e definindo o **esquemas**  propriedade o **XmlValidatingReader** para atribuir o criado **XmlSchemaCollection** para o **XmlValidatingReader**.  
  
### <a name="improved-performance"></a>Desempenho aprimorado  
 É recomendável, se você estiver validando mais de um documento com o mesmo esquema, que você use o **XmlSchemaCollection** porque ele fornece um melhor desempenho fazendo o cache de esquemas na memória.  
  
 O exemplo de código a seguir cria o **XmlSchemaCollection** objeto, adiciona a coleção de esquemas e define o **esquemas** propriedade.  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a>Consulte também  
 [Validação de XDR com XmlSchemaCollection](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [Validação de esquema (XSD) XML com XmlSchemaCollection](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
