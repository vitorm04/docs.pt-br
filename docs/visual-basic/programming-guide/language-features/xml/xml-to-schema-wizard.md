---
title: XML para Assistente de esquema (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlToSchemaWizard
dev_langs:
- VB
helpviewer_keywords:
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
- XML schemas, creating
ms.assetid: 98c495ba-8f37-4517-a0db-aa738611ab76
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d0c9c0247f3d9934ef973c7322cb098f9b445a5a
ms.lasthandoff: 03/13/2017

---
# <a name="xml-to-schema-wizard-visual-basic"></a>Assistente de XML para Esquema (Visual Basic)
Use o Assistente de XML para esquema para criar um conjunto de esquema XML que é inferido de um ou mais documentos XML e incluí-lo em seu projeto. Você pode usar qualquer combinação de documentos XML na forma de arquivos de texto, XML de endereços de HTTP Internet ou XML que é digitado ou colado em XML para Assistente de esquema.  
  
 Esquemas XML são usados para fornecer o IntelliSense para as propriedades XML no Visual Basic. Para obter mais informações, consulte [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) e [XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md).  
  
> [!NOTE]
>  Antes de executar o XML para Assistente de esquema, é recomendável que você remova todos os arquivos XSD existentes do projeto que anteriormente foram geradas pelo assistente. Se você inferir um conjunto de esquema XML que corresponde a um conjunto de esquema existente, pode ocorrer um conflito e [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não será capaz de fornecer o IntelliSense para as propriedades XML.  
  
 O Assistente de XML para esquema usa o <xref:System.Xml.Schema.XmlSchemaInference>classe para criar o esquema para o XML fornecido.</xref:System.Xml.Schema.XmlSchemaInference> Como resultado, vários arquivos de esquema podem ser criados para o conjunto de esquema. Para cada namespace XML no XML fornecido, é criado um arquivo de definição de esquema extensível (XSD). Para obter mais informações, consulte o <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A>método.</xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A>  
  
 Para acessar o Assistente de XML para esquema, clique em **Adicionar Novo Item** no **projeto** menu e adicione um **XML para esquema** modelo do **dados** ou **itens comuns** grupo de modelos. Depois de incluir todas as fontes de documento XML para inferir o conjunto de esquema XML do, clique em **Okey** criar o esquema inferido definido.  
  
 **Tipo de fonte**  
 Esta coluna exibe o tipo da origem de documento XML: **arquivo**, **URL**, ou **XML**.  
  
 **Local do documento XML**  
 Esta coluna exibe o caminho do documento XML. Para documentos XML digitados ou colados, exibe o conteúdo do documento XML.  
  
 **Adicionar de arquivo**  
 Clique neste botão para adicionar arquivos de documento XML usando o Explorador de arquivos.  
  
 **Adicionar a partir da Web**  
 Clique neste botão para fornecer o endereço HTTP de um documento XML.  
  
 **Digite ou cole o XML**  
 Clique neste botão para digitar ou colar um documento XML na caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Schema.XmlSchemaInference></xref:System.Xml.Schema.XmlSchemaInference>   
 [XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)
