---
title: "Assistente de XML para Esquema (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlToSchemaWizard"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "IntelliSense [Visual Basic], XML"
  - "XML [Visual Basic], IntelliSense"
  - "XML IntelliSense [Visual Basic]"
  - "esquemas XML, criando"
ms.assetid: 98c495ba-8f37-4517-a0db-aa738611ab76
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Assistente de XML para Esquema (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Use o assistente de XML para esquema para criar um esquema XML definido que é inferido de um ou vários documentos XML e para incluí\-lo seu projeto.  Você pode usar qualquer combinação de documentos XML na forma de arquivos de texto XML, endereços HTTP Internet, ou XML que está digitada ou colada no assistente de XML para esquema.  
  
 Os esquemas XML são usados para fornecer o IntelliSense para propriedades XML no Visual Basic.  Para obter mais informações, consulte [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) e [XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md).  
  
> [!NOTE]
>  Antes de executar o assistente de XML para esquema, é recomendável que você remove todos os arquivos existentes XSD de projeto que é gerado anteriormente pelo assistente.  Se você infere um esquema XML definido que corresponde a um dataset existente do esquema, pode ocorrer um conflito e [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não poderá fornecer o IntelliSense para propriedades XML.  
  
 O assistente de XML para esquema usa a classe de <xref:System.Xml.Schema.XmlSchemaInference> para criar o esquema XML para fornecido.  Como resultado, os vários arquivos de esquema podem ser criados para o conjunto de esquema.  Para cada namespace XML em XML, extensível fornecido um arquivo de definição de esquema \(XSD\) é criado.  Para obter mais informações, consulte o método <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A>.  
  
 Para acessar o assistente de XML para esquema, clique **Adicionar novo item** no menu de **Projeto** e adicionar um modelo de **XML para Esquema** de **Dados** ou grupo de modelo de **Itens Comuns** .  Depois que você incluiu todas as fontes de documento XML para inferir o esquema XML definido de **OK** , clique em para criar o conjunto inferido de esquema.  
  
 **Tipo de origem**  
 Esta coluna exibe o tipo de fonte de documento XML: **Arquivo**, **URL**, ou **XML**.  
  
 **local de documento XML**  
 Esta coluna exibe o caminho de documento XML.  Para documentos XML tipados ou colados, exibe o conteúdo do documento XML.  
  
 **Adicionar de arquivo**  
 Clique no botão para adicionar arquivos de documentos XML usando Arquivo Explorer.  
  
 **Adicione da Web**  
 Clique no botão para fornecer o endereço HTTP de um documento XML.  
  
 **Digite ou colar XML**  
 Clique no botão para digite ou colar um documento XML na caixa de diálogo.  
  
## Consulte também  
 <xref:System.Xml.Schema.XmlSchemaInference>   
 [XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)