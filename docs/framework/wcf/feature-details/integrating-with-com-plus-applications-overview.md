---
title: Integração com visão geral de aplicativos COM+
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: e481e48f-7096-40eb-9f20-7f0098412941
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c723bda93feac3eef18f302ab0c8ec7c702eb7a
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="integrating-with-com-applications-overview"></a>Integração com visão geral de aplicativos COM+
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Fornece um ambiente rico para criar aplicativos distribuídos. Se você já estiver usando a lógica do aplicativo baseado em componente hospedada em COM+, você pode usar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para estender sua lógica existente em vez de precisar reescrevê-la. Um cenário comum é quando você deseja expor existente lógica de negócios de COM+ ou serviços corporativos por meio de serviços Web.  
  
 Quando uma interface em um componente COM+ é exposta como um serviço Web, a especificação e contrato desses serviços são determinados por um mapeamento automático que é executado em tempo de inicialização do aplicativo. A lista a seguir mostra o modelo conceitual para que esse mapeamento:  
  
-   Um serviço é definido para cada classe COM exposto.  
  
-   O contrato para o serviço é derivado diretamente da definição de interface do componente selecionado com a possibilidade de exclusão do método definido na configuração.  
  
-   As operações no contrato são derivadas diretamente de métodos na definição de interface do componente.  
  
-   Os parâmetros para essas operações são derivados diretamente do tipo de interoperabilidade COM que corresponde aos parâmetros do método do componente.  
  
 Padrão de endereços e associações de transporte para o serviço são fornecidas em um arquivo de configuração de serviço, mas eles podem ser reconfigurados como necessário.  
  
> [!NOTE]
>  Os contratos para os serviços Web expostos permanecem constantes desde que a configuração e interfaces COM+ permanecem inalteradas. Uma modificação em várias interfaces não atualiza automaticamente os serviços disponíveis e requer executar novamente a ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe).  
  
 Os requisitos de autenticação e autorização do aplicativo COM+ e seus componentes continuam a ser aplicada quando usado como um serviço Web.  
  
 Se o chamador inicia uma transação de serviço da Web, componentes marcados como transacional se inscrever nesse escopo de transação.  
  
 As etapas a seguir são necessários para expor a interface do componente COM+ como um serviço Web sem modificar o componente:  
  
1.  Determine se a interface do componente COM+ pode ser exposto como um serviço Web.  
  
2.  Selecione um modo de hospedagem apropriado.  
  
3.  Use a ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe) para adicionar um serviço Web para a interface. Para obter mais informações sobre como usar ComSvcConfig.exe, consulte [como: usar a ferramenta Configuração do modelo de COM+ serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
4.  Configure as configurações de serviço adicionais no arquivo de configuração do aplicativo. Para obter mais informações sobre como configurar um componente, consulte [como: definir configurações de serviço COM+](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md).  
  
## <a name="supported-interfaces"></a>Interfaces com suporte  
 Há algumas restrições no tipo de interfaces que pode ser exposta como um serviço Web. Não há suporte para os seguintes tipos de interfaces:  
  
-   Interfaces que transmitem referências de objeto como parâmetros - a abordagem de referência de objeto limitado a seguir é descrita na seção de suporte limitado de referência de objeto.  
  
-   Interfaces que passam tipos que não são compatíveis com o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] conversões de interoperabilidade COM.  
  
-   Interfaces para aplicativos que têm o pool de aplicativos habilitada quando hospedados pelo COM+.  
  
-   Interfaces de componentes que são marcados como privados para o aplicativo.  
  
-   Interfaces de infraestrutura COM+.  
  
-   Interfaces de aplicativo do sistema.  
  
-   Interfaces de componentes de serviços corporativos que não foram adicionados ao cache de assembly global.  
  
### <a name="limited-object-reference-support"></a>Suporte de referência de objeto limitado  
 Como um número de componentes COM+ implantados usam objetos por parâmetros de referência, como retornar um objeto de conjunto de registros ADO, integração de COM+ inclui suporte limitado para parâmetros de referência de objeto. O suporte é limitado a objetos que implementam o `IPersistStream` interface COM. Isso inclui objetos de conjunto de registros ADO e pode ser implementado para objetos específicos do aplicativo.  
  
 Para habilitar esse suporte, a ferramenta ComSvcConfig.exe fornece o **allowreferences** comutador que desabilita o parâmetro de assinatura de método regular e verifica que a ferramenta é executada para garantir que não estão sendo usados parâmetros de referência de objeto . Além disso, os tipos de objeto que você passa como parâmetros devem ser nomeados e identificados no <`persistableTypes`> elemento de configuração que é um filho de <`comContract`> elemento.  
  
 Quando esse recurso é usado, os usos de serviço de integração COM+ a `IPersistStream` interface para serializar ou desserializar a instância do objeto. Se a instância do objeto não suporta `IPersistStream`, uma exceção será lançada.  
  
 Em um aplicativo cliente, os métodos de <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> objeto pode ser usado para passar um objeto em um serviço e, da mesma forma, para recuperar um objeto.  
  
> [!NOTE]
>  Devido à natureza personalizada e específicos de plataforma da abordagem de serialização, isso é mais adequado para uso entre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços.  
  
## <a name="selecting-the-hosting-mode"></a>Selecionar o modo de hospedagem  
 COM+ expõe serviços da Web em um dos seguintes modos de hospedagem:  
  
-   COM+-hospedado  
  
     O serviço da Web é hospedado dentro COM+ servidor processo dedicado do aplicativo (Dllhost.exe). Esse modo requer que o aplicativo deve ser explicitamente iniciada antes que ele possa receber solicitações de serviço Web. As COM+ opções "Executar como um serviço NT" ou "Deixar executando quando inativo" podem ser usadas para impedir que o desligamento ocioso do aplicativo e seus serviços. Esse modo fornece o serviço Web e acesso DCOM para o aplicativo do servidor.  
  
-   Hospedado na Web  
  
     O serviço da Web é hospedado dentro de um processo de trabalho do servidor Web. Esse modo não requer COM+ esteja ativa quando a solicitação inicial é recebida. Se o aplicativo não estiver ativo quando essa solicitação é recebida, ela é automaticamente ativada antes de processar a solicitação. Este modo também fornece o serviço Web e acesso DCOM para o aplicativo de servidor, mas faz com que um nó de processo para solicitações de serviço Web. Isso geralmente exige que o cliente habilitar a representação. Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], isso pode ser feito com o <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> propriedade do <xref:System.ServiceModel.Security.WindowsClientCredential> classe, que pode é acessada como uma propriedade de genérica <xref:System.ServiceModel.ChannelFactory%601> classe, bem como a <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> valor de enumeração.  
  
-   Web hospedada no processo  
  
     O serviço Web e a lógica do aplicativo COM+ são hospedadas no processo de trabalho do servidor Web. Isso fornece a ativação automática do modo hospedado da Web sem causar um salto de processo para solicitações de serviço Web. A desvantagem é que o aplicativo de servidor não pode ser acessado por meio do DCOM.  
  
### <a name="security-considerations"></a>Considerações sobre segurança  
 Assim como outros [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços, as configurações de segurança para o serviço exposto são administrados por meio de configurações para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] canal. Configurações de segurança DCOM tradicionais, como as configurações de máquina permissões DCOM não são impostas. Para aplicar funções de aplicativo do COM+, autorização "verificações de acesso no nível do componente" deve ser habilitada para o componente.  
  
 O uso de uma associação não é seguro pode deixar comunicação aberta a divulgação de informações ou violação. Para evitar isso, é recomendável que você use uma associação segura.  
  
 Para o COM+-modos hospedados e hospedado na Web, aplicativos cliente devem permitir que o processo do servidor para representar o usuário do cliente. Isso pode ser feito [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes definindo a representação de nível para <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.  
  
 Com os serviços de informações da Internet (IIS) ou o processo de ativação Windows Service (WAS) usando o transporte HTTP, a ferramenta Httpcfg.exe pode ser usada para reservar um endereço de ponto de extremidade de transporte. Em outras configurações, é importante proteger contra serviços mal-intencionados que agem como o serviço pretendido. Para impedir a inicialização no ponto de extremidade desejado de um serviço autorizado, o serviço legítimo pode ser configurado para ser executado como um serviço NT. Isso permite que o serviço legítimo declarar o endereço do ponto de extremidade antes de qualquer serviço autorizado.  
  
 Ao expor um aplicativo COM+ com funções COM+ configurados como um serviço hospedado na Web, a "conta de processo de IIS iniciar" deve ser adicionada a uma das funções do aplicativo. Essa conta, normalmente com o nome IWAM_machinename, deve ser adicionada para permitir desligamento normal de objetos após o uso. A conta não deve receber as permissões adicionais.  
  
 O processo COM+ reciclagem de recursos não pode ser usado em aplicativos integrados. Se o aplicativo está configurado para usar a reciclagem de processo e os componentes estão em execução em um processo hospedados pelo COM+, o serviço não for iniciado. Esse requisito não inclui serviços usando o modo de-processo hospedado na Web porque não são aplicadas as configurações de reciclagem do processo.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da integração de aplicativos COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
