---
title: Adotando o Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 15fc02882148054fe53534c75905f51cfffe68fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="adopting-windows-communication-foundation"></a>Adotando o Windows Communication Foundation
Você pode optar por usar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para novos desenvolvimentos, enquanto continua a manter os aplicativos existentes desenvolvidos usando o ASP.NET. Porque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é deve ser a escolha mais adequada para facilitar a comunicação com os aplicativos criados com o .NET Framework em qualquer cenário, pode servir como uma ferramenta padrão para resolver uma ampla variedade de problemas de comunicação de software de forma não é possível que o ASP.NET.  
  
 Novo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos podem ser implantados nas mesmas máquinas como serviços Web ASP.NET existentes. Se os serviços da Web ASP.NET existentes usam uma versão do .NET Framework anteriores à versão 2.0, você pode usar a ferramenta de registro ASP.NET IIS para implantar seletivamente o .NET Framework 2.0 para aplicativos do IIS no qual o novo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos devem ser hospedadas. Essa ferramenta está documentada em [ferramenta de registro ASP.NET IIS (Aspnet_regiis.exe)](http://go.microsoft.com/fwlink/?LinkId=94687), e tem uma interface de usuário criado no console de gerenciamento do IIS 6.0.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]pode ser usado para adicionar novos recursos para os serviços Web ASP.NET existentes adicionando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços configurados para executar no modo de compatibilidade ASP.NET para aplicativos de serviço da Web do ASP.NET no IIS. Devido ao modo de compatibilidade do ASP.NET, o código para o novo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços podem acessar e atualizar as mesmas informações de estado do aplicativo que o código ASP.NET já existente, usando o <xref:System.Web.HttpContext> classe. Os aplicativos também podem compartilhar as mesmas bibliotecas de classe.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]os clientes podem usar os serviços Web do ASP.NET. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]serviços que são configurados com o <xref:System.ServiceModel.BasicHttpBinding> pode ser usado por clientes de serviço Web do ASP.NET. Serviços Web do ASP.NET podem coexistir com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos, e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ainda pode ser usado para adicionar recursos a serviços Web ASP.NET existentes. Considerando todas essas situações em que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e serviços da Web ASP.NET podem ser usados juntos, você pode migrar os serviços Web do ASP.NET para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] somente se você precisar de recursos que são fornecidos pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e não os serviços Web do ASP.NET.  
  
 Até mesmo em alguns casos em que é necessário, considere cuidadosamente migrando o código de uma tecnologia para outro raramente é a abordagem correta. É o motivo para adotar a nova tecnologia atender aos novos requisitos que não podem ser atendidos com a tecnologia anterior e, nesse caso, a ação correta é criar uma nova solução para atender o conjunto de requisitos recentemente expandido. Os novos benefícios de design de sua experiência com o sistema existente em sabedoria decorrente desde que o sistema foi projetado. O novo design também pode usar os recursos completos de novas tecnologias em vez de reproduzir o design antigo na nova plataforma. Depois de elementos principais de protótipos do novo projeto, fica mais fácil para reutilizar o código do sistema existente em uma nova.  
  
 Para alguns casos onde portabilidade do ASP.NET Web services para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é a solução correta, a seção a seguir fornece algumas diretrizes sobre como proceder. Não há sugestões sobre como migrar serviços e como migrar clientes.  
  
 Para obter uma análise completa sobre como migrar serviços de Web do ASP.NET existentes para o WCF, consulte [serviços Web ASP.NET e o Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkID=71761). Esta seção descreve como implementar um serviço WCF compatível com dos metadados para que o serviço Web ASP.NET e como migrar o código de cliente e de serviço da Web do ASP.NET para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Como: recuperar metadados e implementar um serviço compatível](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)  
 [Como: migrar o código de serviço da Web do ASP.NET para o Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)  
 [Como: migrar o código de cliente de serviço da Web do ASP.NET para o Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
