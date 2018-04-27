---
title: Ordem de serialização personalizada com o XmlSerializer
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b091d07ada0031013c935c5ab12b77ebedd6bcc3
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="custom-serialization-order-with-xmlserializer"></a>Ordem de serialização personalizada com o XmlSerializer
[Baixar Exemplo](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 Esse exemplo mostra como controlar a ordem de elementos serializados e desserializados para serialização de XML.  
  
 Revise os comentários no código de origem e nos arquivos build.proj para obter mais informações sobre serialização.  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Para criar o exemplo usando o Prompt de Comando  
  
1.  Abra a janela do Prompt de Comando e navegue para um dos subdiretórios específicos da linguagem para o exemplo.  
  
2.  Digite **msbuild CustomOrder.sln** na linha de comando.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Para criar o exemplo usando Visual Studio  
  
1.  Abra o [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] e navegue para um dos subdiretórios específicos da linguagem para o exemplo.  
  
2.  Clique duas vezes no ícone para o CustomOrder.sln para abrir o arquivo no Visual Studio.  
  
3.  No menu **Compilar**, selecione **Compilar Solução**.  
  
4.  O aplicativo de exemplo será criado no subdiretório padrão \bin ou \bin\Debug.  
  
## <a name="see-also"></a>Consulte também  
 [Serialização básica](../../../docs/standard/serialization/basic-serialization.md)  
 [Serialização binária](../../../docs/standard/serialization/binary-serialization.md)  
 [Controlando a serialização XML usando atributos](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [Apresentando a serialização XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [Serialização](../../../docs/standard/serialization/index.md)  
 [Serialização XML e SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
