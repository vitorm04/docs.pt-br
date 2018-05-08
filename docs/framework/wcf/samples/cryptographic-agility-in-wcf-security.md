---
title: Agilidade criptográfica de segurança do WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5fa4c3cf45eb17822effaa9284864274923b2504
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cryptographic-agility-in-wcf-security"></a>Agilidade criptográfica de segurança do WCF
Este exemplo mostra como especificar um algoritmo de standard/personalizada para fornecer uma implementação criptográfica agile em um cliente Windows Communication Foundation (WCF) e o serviço. O exemplo é composto dos seguintes projetos:  
  
 Serviço  
 Este é um auto-hospedado [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço que implementa o `ICalculator` interface e protege o ponto de extremidade usando o <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> com a sessão segura e confiável de sessão desabilitada. O serviço define um personalizado `SecurityAlgorithmSuite` classe para especificar os algoritmos de criptografia a ser usado para segurança de mensagem.  
  
 Cliente  
 Este é um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]cliente que acessa o serviço após a autenticação bem-sucedida. Invocar operações expostas pelo `ICalculator` interface e implementados pelo serviço. O cliente também define o mesmo personalizado `SecurityAlgorithmSuite` classe para especificar os algoritmos de criptografia a ser usado para segurança de mensagem.  
  
### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra a solução CryptoAgility.sln em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Pressione CTRL+SHIFT+B para criar a solução.  
  
3.  Abra [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] e navegue até o diretório \WCF\Basic\Security\CryptoAgility\Service\bin e execute o arquivo de service.exe com privilégios de administrador, clicando duas vezes service.exe e selecionando **executar como administrador**.  
  
4.  Navegue até o diretório \WCF\Basic\Security\CryptoAgility\Client\bin e execute o arquivo client.exe normalmente.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a>Consulte também  
 [Segurança](../../../../docs/framework/wcf/feature-details/security.md)
