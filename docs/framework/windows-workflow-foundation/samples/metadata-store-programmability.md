---
title: Programabilidade de Store de metadados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b8bfce17169a1095d2d2817467fcc8f3366ead3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="metadata-store-programmability"></a>Programabilidade de Store de metadados
O armazenamento de metadados é um recurso de [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] que permite a associação de metadados arbitrários, na forma de atributos CLR, para tipos em tempo de execução. Isso permite que um acoplamento fraco entre os componentes de tempo de execução e suas contrapartes em tempo de design, bem como a capacidade alterar os componentes de tempo de design sem afetar o tempo de execução. O exemplo mostra como programar no armazenamento de metadados aplicando atributos para um tipo de tempo de execução, a fonte para que nós não tem controle sobre. A terminologia usada normalmente é que um aplicativo hospedeiro registra os metadados para um conjunto de tipos.  
  
 Na saída, você pode perceber um atributo adicional, inesperado, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`. Isso é adicionado ao usar os metadados API e não tem impacto no exemplo.  
  
 Este exemplo demonstra:  
  
## <a name="demonstrates"></a>Demonstra  
  
-   A inclusão de atributo que usa metadados armazena API.  
  
-   Usando um mecanismo de retorno de chamada para adiar o registro de metadados.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de ProgrammingMetadataStore.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`