---
title: Integração com visão geral de aplicativos COM+
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: e481e48f-7096-40eb-9f20-7f0098412941
ms.openlocfilehash: b5294080d0cc76fdb98bc0908f4273dbb011f982
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328719"
---
# <a name="integrating-with-com-applications-overview"></a>Integração com visão geral de aplicativos COM+
Windows Communication Foundation (WCF) fornece um ambiente avançado para criar aplicativos distribuídos. Se você já estiver usando a lógica de aplicativo baseado em componente hospedada em COM+, você pode usar o WCF para estender sua lógica existente em vez de precisar reescrevê-la. Um cenário comum é quando você deseja expor COM+ ou serviços corporativos lógica de negócios existentes por meio de serviços da Web.  
  
 Quando uma interface em um componente COM+ é exposta como um serviço Web, a especificação e um contrato de um desses serviços são determinados por um mapeamento automático que é executado em tempo de inicialização do aplicativo. A lista a seguir mostra o modelo conceitual para esse mapeamento:  
  
-   Um serviço é definido para cada classe do COM expostos.  
  
-   O contrato do serviço será derivado diretamente da definição de interface do componente selecionado com a possibilidade de exclusão do método definido na configuração.  
  
-   As operações nesse contrato derivam diretamente os métodos de definição de interface do componente.  
  
-   Os parâmetros para essas operações são derivados diretamente do tipo de interoperabilidade de COM que corresponde aos parâmetros do método do componente.  
  
 Padrão de endereços e associações de transporte para o serviço são fornecidas em um arquivo de configuração de serviço, mas eles podem ser reconfigurados como necessário.  
  
> [!NOTE]
>  Os contratos para os serviços Web expostos permanecem constantes, desde a interfaces COM+ e a configuração permanecem inalterados. Uma modificação em várias interfaces não atualiza automaticamente os serviços disponíveis e exige executar novamente a ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe).  
  
 Os requisitos de autenticação e autorização do aplicativo COM+ e seus componentes continuam a ser imposta quando usado como um serviço Web.  
  
 Se o chamador inicia uma transação de serviço da Web, componentes marcados como transacional inscrever-se dentro do escopo da transação.  
  
 As etapas a seguir são necessários para expor a interface de um componente COM+ como um serviço Web sem modificar o componente:  
  
1. Determine se a interface do componente COM+ pode ser exposto como um serviço Web.  
  
2. Selecione um modo de hospedagem apropriado.  
  
3. Use a ferramenta de configuração de modelo de serviço COM+ (ComSvcConfig.exe) para adicionar um serviço Web para a interface. Para obter mais informações sobre como usar ComSvcConfig.exe, consulte [como: Use a ferramenta de configuração de modelo de serviço COM+](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
4. Configure as configurações de serviço adicionais no arquivo de configuração do aplicativo. Para obter mais informações sobre como configurar um componente, consulte [como: Definir as configurações de serviço COM+](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md).  
  
## <a name="supported-interfaces"></a>Interfaces com suporte  
 Há algumas restrições sobre o tipo de interfaces que podem ser expostos como um serviço Web. Não há suporte para os seguintes tipos de interfaces:  
  
-   Interfaces que transmitem referências de objeto como parâmetros - a seguinte abordagem de referência de objeto limitada é descrita na seção de suporte limitado de referência de objeto.  
  
-   Interfaces que passam tipos que não são compatíveis com o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] conversões de interoperabilidade COM.  
  
-   Interfaces para aplicativos que têm o pool de aplicativo ativado quando hospedado por COM+.  
  
-   Interfaces de componentes que são marcados como particulares ao aplicativo.  
  
-   Interfaces de infra-estrutura COM+.  
  
-   Interfaces de aplicativo do sistema.  
  
-   Interfaces de componentes de serviços corporativos que não foram adicionados ao cache de assembly global.  
  
### <a name="limited-object-reference-support"></a>Suporte de referência de objeto limitada  
 Como um número de componentes COM+ implantados usam objetos por parâmetros de referência, como retornar um objeto de conjunto de registros ADO, integração de COM+ inclui suporte limitado para parâmetros de referência de objeto. O suporte é limitado a objetos que implementam o `IPersistStream` interface COM. Isso inclui objetos de conjunto de registros ADO e pode ser implementado para objetos específicos do aplicativo.  
  
 Para habilitar esse suporte, a ferramenta ComSvcConfig.exe fornece o **allowreferences** comutador que desabilita o parâmetro de assinatura de método regular e verifica que a ferramenta é executada para garantir que não estão sendo usados parâmetros de referência de objeto . Além disso, os tipos de objeto que você passa como parâmetros devem ser nomeados e identificados no <`persistableTypes`> elemento de configuração que é um filho de <`comContract`> elemento.  
  
 Quando esse recurso é usado, os usos de serviço de integração COM+ o `IPersistStream` interface para serializar ou desserializar a instância do objeto. Se a instância do objeto não dá suporte `IPersistStream`, uma exceção será lançada.  
  
 Dentro de um aplicativo cliente, os métodos no <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> objeto pode ser usado para passar um objeto em um serviço e, da mesma forma, para recuperar um objeto.  
  
> [!NOTE]
>  Devido à natureza personalizada e específicos da plataforma da abordagem de serialização, isso é mais adequado para uso entre os clientes do WCF e serviços WCF.  
  
## <a name="selecting-the-hosting-mode"></a>Selecionar o modo de hospedagem  
 COM+ expõe serviços da Web em um dos seguintes modos de hospedagem:  
  
-   COM+-hospedados  
  
     O serviço Web é hospedado dentro COM+ server processo dedicado do aplicativo (Dllhost.exe). Esse modo requer que o aplicativo para ser iniciada explicitamente que ela possa receber solicitações de serviço Web. As COM+ opções "Executar como um serviço NT" ou "Em execução quando ocioso Leave" podem ser usadas para impedir que o desligamento quando ocioso do aplicativo e seus serviços. Esse modo fornece o serviço Web e acesso DCOM para o aplicativo de servidor.  
  
-   Hospedado na Web  
  
     O serviço Web é hospedado dentro de um processo de trabalho do servidor Web. Esse modo não requer COM+ esteja ativa quando a solicitação inicial é recebida. Se o aplicativo não está ativo quando essa solicitação é recebida, ela será ativada automaticamente antes de processar a solicitação. Esse modo também fornece acesso DCOM para o aplicativo de servidor e serviço da Web, mas faz com que um salto de processo para solicitações de serviço Web. Isso normalmente requer que o cliente habilitar a representação. No WCF, isso pode ser feito com o <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> propriedade do <xref:System.ServiceModel.Security.WindowsClientCredential> classe, que pode é acessado como uma propriedade de genérica <xref:System.ServiceModel.ChannelFactory%601> classe, bem como o <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> valor de enumeração.  
  
-   Hospedado na Web em processo  
  
     O serviço Web e a lógica do aplicativo COM+ são hospedados dentro do processo de trabalho do servidor Web. Isso fornece a ativação automática do modo hospedado na Web sem causar um salto de processo para solicitações de serviço Web. A desvantagem é que o aplicativo de servidor não pode ser acessado por meio do DCOM.  
  
### <a name="security-considerations"></a>Considerações sobre segurança  
 Como outros serviços do WCF, as configurações de segurança para o serviço exposto são administradas por meio de definições de configuração para o canal do WCF. Configurações de segurança DCOM tradicionais, como as configurações de todo o computador permissões DCOM não são impostas. Para impor as funções de aplicativo COM+, as "verificações de acesso no nível do componente" autorização deve ser habilitada para o componente.  
  
 O uso de uma associação não é seguro pode deixar comunicação aberta à divulgação de informações ou violação. Para evitar isso, é recomendável que você use uma associação segura.  
  
 Para o COM+-modos hospedados e hospedados na Web, aplicativos cliente devem permitir que o processo do servidor para representar o usuário do cliente. Isso pode ser feito em clientes do WCF, definindo a representação de nível para <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.  
  
 Com os serviços de informações da Internet (IIS) ou Windows processo de ativação do WAS (serviço) usando o transporte HTTP, a ferramenta de Httpcfg.exe pode ser usada para reservar um endereço de ponto de extremidade de transporte. Em outras configurações, é importante proteger contra serviços mal-intencionados que agem como o serviço pretendido. Para impedir que um serviço invasor começando no ponto de extremidade desejado, o serviço de legítimo pode ser configurado para ser executado como um serviço NT. Isso permite que o serviço legítimos solicitar o endereço do ponto de extremidade antes de quaisquer serviços mal-intencionados.  
  
 Ao expor um aplicativo COM+ com funções COM+ configurados como um serviço hospedado na Web, a "conta de processo de IIS iniciar" deve ser adicionada a uma das funções do aplicativo. Essa conta, normalmente com o nome IWAM_machinename, deve ser adicionada para habilitar o desligamento normal de objetos após o uso. A conta não deve receber nenhuma permissão adicional.  
  
 O processo de COM+ reciclagem de recursos não pode ser usado em aplicativos integrados. Se o aplicativo está configurado para usar a reciclagem de processo e os componentes estão em execução em um processo hospedada em COM+, o serviço não for iniciado. Esse requisito não inclui serviços usando o modo em processo hospedado na Web porque não são aplicadas as configurações de reciclagem de processo.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da integração de aplicativos COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
