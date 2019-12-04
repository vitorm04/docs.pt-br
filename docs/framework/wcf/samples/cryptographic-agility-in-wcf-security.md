---
title: Agilidade de criptografia na segurança do WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 2dbacd53876ded76ea212dd5656cd2dded4a6e48
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714933"
---
# <a name="cryptographic-agility-in-wcf-security"></a>Agilidade de criptografia na segurança do WCF

Este exemplo mostra como especificar em um algoritmo padrão/personalizado para fornecer uma implementação ágil de criptografia em um cliente e serviço do Windows Communication Foundation (WCF). O exemplo é composto pelos seguintes projetos:

**Serviço**

Este é um serviço WCF auto-hospedado que implementa a interface `ICalculator` e protege o ponto de extremidade usando o <xref:System.ServiceModel.WSHttpBinding> com sessão segura e sessão confiável desabilitada. O serviço define uma classe de `SecurityAlgorithmSuite` personalizada para especificar os algoritmos criptográficos a serem usados para segurança de mensagens.

**Cliente**

Esse é um cliente WCF que acessa o serviço após a autenticação bem-sucedida. Ele invoca as operações expostas pela interface `ICalculator` e implementada pelo serviço. O cliente também define a mesma classe de `SecurityAlgorithmSuite` personalizada para especificar os algoritmos criptográficos a serem usados para segurança de mensagens.

## <a name="to-use-this-sample"></a>Para usar este exemplo

1. Abra a solução CryptoAgility. sln no Visual Studio 2012.

2. Pressione CTRL+SHIFT+B para criar a solução.

3. Abra o explorador de arquivos e navegue até o diretório \WCF\Basic\Security\CryptoAgility\Service\bin e execute o arquivo Service. exe com privilégios de administrador clicando com o botão direito do mouse em Service. exe e selecionando **Executar como administrador**.

4. Navegue até o diretório \WCF\Basic\Security\CryptoAgility\Client\bin e execute o arquivo client. exe normalmente.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a>Consulte também

- [Segurança de Windows Communication Foundation](../feature-details/security.md)
