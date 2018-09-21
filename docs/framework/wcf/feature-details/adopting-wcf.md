---
title: Adotando o Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: 5773d2687eb06cfc562dbe25fa9b94864b1b3a49
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46538866"
---
# <a name="adopting-windows-communication-foundation"></a>Adotando o Windows Communication Foundation

Você pode optar por usar o Windows Communication Foundation (WCF) para novos desenvolvimentos, enquanto continua a manter os aplicativos existentes desenvolvidos usando o ASP.NET. Porque o WCF deve ser a escolha mais adequada para facilitar a comunicação com os aplicativos criados com o .NET Framework em qualquer cenário, ele pode servir como uma ferramenta padrão para resolver uma ampla variedade de problemas de comunicação de software de forma que o ASP.NET não é possível.

Novos aplicativos do WCF podem ser implantados nos mesmos computadores como serviços Web do ASP.NET existentes. Se os serviços Web do ASP.NET existentes usam uma versão do .NET Framework anteriores à versão 2.0, você pode usar a ferramenta de registro ASP.NET IIS implantar seletivamente o .NET Framework 2.0 em aplicativos do IIS em que novos aplicativos do WCF devem ser hospedadas. Essa ferramenta está documentada em [ferramenta de registro ASP.NET IIS (Aspnet_regiis.exe)](https://go.microsoft.com/fwlink/?LinkId=94687), e tem uma interface de usuário integrada no console de gerenciamento do IIS 6.0.

O WCF pode ser usado para adicionar novos recursos para os serviços Web do ASP.NET existentes, adicionando os serviços WCF configurados para ser executado no modo de compatibilidade do ASP.NET para aplicativos de serviço Web ASP.NET existentes no IIS. Devido ao modo de compatibilidade do ASP.NET, o código para os novos serviços WCF pode acessar e atualizar as informações de estado do aplicativo mesmo que o código ASP.NET já existente, usando o <xref:System.Web.HttpContext> classe. Os aplicativos também podem compartilhar as mesmas bibliotecas de classe.

Clientes do WCF podem usar os serviços Web do ASP.NET. Os serviços WCF que são configurados com o <xref:System.ServiceModel.BasicHttpBinding> pode ser usado por clientes de serviço Web do ASP.NET. Serviços Web do ASP.NET podem coexistir com os aplicativos do WCF e WCF ainda pode ser usado para adicionar recursos a serviços Web do ASP.NET existentes. Considerando todas essas formas em que os serviços WCF e ASP.NET Web podem ser usados juntos, você talvez queira migrar serviços Web do ASP.NET ao WCF somente se você precisar de recursos que são fornecidos pelos serviços WCF e não da Web do ASP.NET.

Até mesmo em alguns casos em que é necessário, migrando o código de uma tecnologia para outro raramente é a abordagem correta. O motivo para adotar a nova tecnologia é para atender aos novos requisitos que não podem ser atendidos com a tecnologia anterior e, nesse caso, a coisa correta a fazer é criar uma nova solução para atender o conjunto de requisitos recentemente expandido. Os novos benefícios de design de sua experiência com o sistema existente e de sabedoria ganhou uma vez que esse sistema foi projetado. O novo design também pode usar os recursos completos de novas tecnologias em vez de reproduzir o design antigo na nova plataforma. Após a criação de protótipos elementos-chave o novo design, fica mais fácil para reutilização de código do sistema existente dentro de um novo.

## <a name="see-also"></a>Consulte também

- [Como recuperar metadados e implementar um serviço em conformidade](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
