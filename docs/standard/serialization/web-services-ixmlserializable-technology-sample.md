---
title: "Exemplo de tecnologia IXmlSerializable de serviços Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: be0c76371bda9e91e0becf8a9e09beb44e44dd3c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="web-services-ixmlserializable-technology-sample"></a>Exemplo de tecnologia IXmlSerializable de serviços Web
[Baixar Exemplo](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 Esse exemplo mostra como usar o <xref:System.Xml.Serialization.IXmlSerializable> para controlar a serialização de tipos personalizados em Serviços Web ASP.NET.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Para criar o exemplo usando Visual Studio  
  
1.  Abra o [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] e selecione **Novo Site** no menu **Arquivo**.  
  
2.  No painel esquerdo da caixa de diálogo **Novo Site**, selecione a linguagem de programação desejada e, em seguida, no painel esquerdo, selecione **Serviço Web ASP.NET**.  
  
3.  Digite **IXmlSerializable** como o nome do novo serviço Web.  
  
4.  Na janela do Gerenciador de Soluções, clique com o botão direito do mouse no ícone de Service.asmx e selecione **Excluir**; repita essa etapa para o arquivo code-behind Service.asmx.  
  
5.  Clique com o botão direito do mouse no diretório do projeto e selecione **Adicionar Item Existente**. Na caixa de diálogo, navegue para o subdiretório de Serviço do diretório específico da linguagem.  
  
6.  Selecione Service.asmx e, em seguida, repita essa etapa para o arquivo codebehind Service.asmx.  
  
7.  Abra o [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] e navegue para o diretório que contém o diretório IXmlSerializable que você criou na etapa 3 acima.  
  
8.  Clique com o botão direito do mouse no ícone do diretório IXmlSerializable e selecione **Compartilhamento e Segurança**.  
  
9. Na guia Compartilhamento da Web, selecione **Compartilhar esta Pasta** e confirme as configurações padrão, incluindo o nome IXmlSerializable.  
  
10. Clique em **OK**.  
  
### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra uma janela do navegador e selecione sua barra de endereços.  
  
2.  Digite **http://localhost/IXmlSerializable/Service.asmx**.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization>  
 <xref:System.Xml.XmlConvert>  
 <xref:System.Xml.XmlQualifiedName>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.XmlSchema>  
 <xref:System.Xml.Schema.XmlSchemaSet>  
 <xref:System.Xml.XmlUrlResolver>  
 <xref:System.Xml.XmlWriter>
