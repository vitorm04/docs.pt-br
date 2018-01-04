---
title: "Gerenciamento de declarações e autorizações com o modelo de identidade"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authorization [WCF]
- WCF security
- claims [WCF], managing with the Identity Model
- claims [WCF]
- authorization [WCF], managing with the Identity Model
ms.assetid: 099defbb-5d35-434e-9336-1a49b9ec7663
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db0a304a908e906b635672eed1a84f0277284ad7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="managing-claims-and-authorization-with-the-identity-model"></a>Gerenciamento de declarações e autorizações com o modelo de identidade
A autorização é o processo de determinar quais entidades têm permissão para alterar, exibir ou, caso contrário, acessar um recurso de computador. Por exemplo, em uma empresa, somente os gerentes podem permitidos para acessar os arquivos de seus funcionários. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]oferece suporte a dois mecanismos para executar o processamento de autorização. O primeiro mecanismo permite que você controle a autorização usando existente construções de runtime (CLR) de linguagem comum. O segundo é um modelo baseado em declarações, conhecido como o *modelo de identidade*. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa o modelo de identidade para criar declarações de mensagens de entrada; Classes de modelo de identidade podem ser estendidos para dar suporte a novos tipos de declaração para esquemas de autorização personalizada. Este tópico apresenta uma visão geral de como os principais conceitos de programação do recurso de modelo de identidade, bem como uma lista das classes mais importantes que usa o recurso.  
  
## <a name="identity-model-scenarios"></a>Cenários de modelo de identidade  
 Os cenários a seguir representam o uso do modelo de identidade.  
  
### <a name="scenario-1-supporting-identity-role-and-group-claims"></a>Cenário 1: Suporte a identidade, a função e as declarações de grupo  
 Os usuários enviar mensagens para um serviço Web. Os requisitos de controle de acesso do serviço Web usam identidades, funções ou grupos. O remetente da mensagem é mapeado para um conjunto de funções ou grupos. Informações de função ou grupo são usadas para executar verificações de acesso.  
  
### <a name="scenario-2-supporting-rich-claims"></a>Cenário 2: Suporte a declarações avançada  
 Os usuários enviar mensagens para um serviço Web. Os requisitos de controle de acesso do serviço Web exigem um modelo mais avançado de identidade, funções ou grupos. O serviço Web determina se um determinado usuário tem acesso a um determinado recurso protegido usando o modelo avançado baseado em declarações. Por exemplo, um usuário pode ser capaz de ler informações específicas, como informações de salário, que outros usuários não têm acesso ao.  
  
### <a name="scenario-3-mapping-disparate-claims"></a>Cenário 3: Mapeamento de declarações diferentes  
 Um usuário envia uma mensagem para um serviço Web. O usuário pode especificar suas credenciais de várias maneiras diferentes: certificado x. 509, o token de nome de usuário ou o token Kerberos. O serviço Web é necessário para executar verificações de controle de acesso da mesma maneira, independentemente do tipo de credencial do usuário. Se há suporte para tipos de credenciais adicionais ao longo do tempo, o sistema deve evoluir adequadamente.  
  
### <a name="scenario-4-determining-access-to-multiple-resources"></a>Cenário 4: Determinar o acesso a vários recursos  
 Um serviço da Web tenta acessar vários recursos. O serviço determina quais recursos protegidos de um determinado usuário tem acesso, comparando as declarações associadas ao usuário com as declarações necessárias para acessar o recurso.  
  
## <a name="identity-model-terms"></a>Termos de modelo de identidade  
 A lista a seguir define os principais termos usados para descrever os conceitos de modelo de identidade.  
  
 Política de autorização  
 Um conjunto de regras para o mapeamento de um conjunto de declarações de entrada para um conjunto de declarações de saída. Avaliar resultados de diretiva de autorização na declaração conjuntos que está sendo adicionados a um contexto de avaliação e, subsequentemente, um contexto de autorização.  
  
 Contexto de autorização  
 Um conjunto de conjuntos de declarações e zero ou mais propriedades. O resultado da avaliação de uma ou mais políticas de autorização.  
  
 Declaração  
 Uma combinação de um tipo de declaração, à direita e um valor.  
  
 Conjunto de declarações  
 Um conjunto de declarações emitidas por um emissor específico.  
  
 Tipo de declaração  
 Um tipo de declaração. Declarações definidas pela API do modelo de identidade são propriedades da <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> classe. Exemplos de tipos de declaração fornecida pelo sistema são <xref:System.IdentityModel.Claims.ClaimTypes.Dns%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Email%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Hash%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Sid%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Spn%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.System%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Uri%2A>, e <xref:System.IdentityModel.Claims.ClaimTypes.X500DistinguishedName%2A>.  
  
 contexto de avaliação  
 Um contexto no qual uma política de autorização é avaliada. Contém conjuntos de propriedades e declarações. Se torna a base de um contexto de autorização após a conclusão da avaliação.  
  
 Declaração de identidade  
 Uma declaração cuja direita é a identidade.  
  
 Emissor  
 Um conjunto de declarações que contém pelo menos uma declaração de identidade e é considerado emitiu outro conjunto de declarações.  
  
 Propriedades  
 Um conjunto de informações associadas a um contexto de avaliação ou contexto de autorização.  
  
 Recurso protegido  
 Algo no sistema que só pode ser usado, acessado ou manipulado se determinados requisitos forem atendidos pela primeira vez.  
  
 Direita  
 Um recurso em um recurso. Direitos definidos pela API do modelo de identidade são propriedades da <xref:System.IdentityModel.Claims.Rights> classe. Exemplos de direitos fornecido pelo sistema são <xref:System.IdentityModel.Claims.Rights.Identity%2A> e <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.  
  
 Valor  
 Algo sobre o qual um direito é solicitado.  
  
## <a name="claims"></a>declarações  
 O modelo de identidade é um sistema baseado em declarações. Declarações descrevem os recursos associados a uma entidade no sistema, geralmente um usuário do sistema. O conjunto de declarações associado a uma determinada entidade pode ser pensado como uma chave. As declarações específicas definem a forma de chave, semelhante a uma chave física usada para abrir um bloqueio em uma porta. Declarações são usadas para obter acesso aos recursos. Acesso a um determinado recurso protegido é determinado comparando as declarações necessárias para acessar o recurso com as declarações associadas ao acesso de tentativa de entidade.  
  
 Uma declaração é a expressão de um direito em relação a um valor específico. Um direito poderia ser algo como "Leitura", "Gravação" ou "Executar". Um valor pode ser um banco de dados, um arquivo, uma caixa de correio ou uma propriedade. Declarações também têm um tipo de declaração. A combinação de tipo de declaração e direita fornece o mecanismo para especificar recursos em relação o valor. Por exemplo, uma declaração do tipo "File", "Leitura" direito sobre o valor "Biography.doc" indica que a entidade à qual essa uma declaração está associada tem acesso de leitura ao arquivo Biography.doc. Uma declaração de tipo "Name", com o direito "PossessProperty" sobre o valor "Martin" indica que a entidade à qual essa uma declaração está associada possui uma propriedade de nome com o valor "Martin".  
  
 Embora vários tipos de declaração de direitos são definidos como parte do modelo de identidade, o sistema é extensível, permitindo que vários sistemas, criando sobre a infraestrutura do modelo de identidade, para definir direitos e tipos de declaração adicionais conforme necessário.  
  
### <a name="identity-claims"></a>Declarações de identidade  
 Um direito específico é de identidade. Declarações que possuem esse direito de fazem uma instrução sobre a identidade da entidade. Por exemplo, uma declaração de tipo "user principal name" (UPN) com um valor de "someone@example.com" e um direito de identidade indica uma identidade específica em um domínio específico.  
  
#### <a name="system-identity-claim"></a>Declaração de identidade do sistema  
 O modelo de identidade define uma declaração de identidade: System. A declaração de identidade do sistema indica que uma entidade é o aplicativo atual ou o sistema.  
  
### <a name="sets-of-claims"></a>Conjuntos de declarações  
 O modelo de declarações que representam a identidade é importante porque as declarações são sempre emitidas por uma entidade no sistema, mesmo se essa entidade é, por fim, alguns conceito de "auto". Declarações são agrupadas juntos como um conjunto e cada conjunto tem um emissor. Um emissor é apenas um conjunto de declarações. Essa relação recursiva eventualmente deve terminar e conjunto pode ser seu próprio emissor de declaração.  
  
 A figura a seguir mostra um exemplo dos três conjuntos de declarações, onde um conjunto de declarações tem, como o emissor, outro conjunto de declarações, que por sua vez tem o sistema estiver definida como o emissor de declaração. Portanto, os conjuntos de declarações formam uma hierarquia que pode ser arbitrariamente profunda.  
  
 ![Gerenciando reivindicações e autorização](../../../../docs/framework/wcf/feature-details/media/claimshierarchy.gif "claimshierarchy")  
  
 Vários conjuntos de declarações podem ter o mesmo de emissão de declaração de conjunto, conforme ilustrado na figura a seguir.  
  
 ![Gerenciando reivindicações e autorização](../../../../docs/framework/wcf/feature-details/media/multiplesetsofclaims.gif "multiplesetsofclaims")  
  
 Com exceção de um conjunto de declarações que é seu próprio emissor, o modelo de identidade não fornece nenhum suporte para conjuntos de declarações formar um loop. Portanto, nunca pode surgir uma situação em que um conjunto de declarações é emitido pelo conjunto de declaração B, que também é emitido por um conjunto de declarações. Além disso, o modelo de identidade não fornece nenhum suporte para conjuntos de declarações ter vários emissores. Se dois ou mais emissores devem emitir um determinado conjunto de declarações, você deve usar vários conjuntos de declarações, cada um contendo as declarações a mesmas, mas com diferentes emissores.  
  
### <a name="the-origin-of-claims"></a>A origem das declarações  
 Declarações podem vir de uma variedade de fontes. Uma fonte comum de declarações é as credenciais apresentadas por um usuário, por exemplo, como parte de uma mensagem enviada a um serviço Web. O sistema confirmará essas declarações, e eles se tornarão parte de um conjunto de declarações associada ao usuário. Outros componentes do sistema também podem ser fontes de declarações, incluindo, mas não limitado a, o sistema operacional, a pilha de rede, o ambiente de tempo de execução ou o aplicativo. Além disso, os serviços remota também podem ser uma fonte de declarações.  
  
### <a name="authorization-policies"></a>Diretivas de autorização  
 O modelo de identidade, as declarações são geradas como parte do processo de avaliação da política de autorização. Uma política de autorização examina o conjunto (possivelmente vazio) de declarações existentes e pode optar por adicionar declarações adicionais baseadas nas declarações estiver presentes e informações adicionais à sua disposição. Isso fornece a base para mapeamento entre declarações. A presença ou ausência de declarações no sistema influencia o comportamento de uma política de autorização em relação ao se adicionar declarações adicionais.  
  
 Por exemplo, a política de autorização tem acesso a um banco de dados que inclui as datas de nascimento das várias entidades usando o sistema. A política de autorização usa essas informações para adicionar uma declaração de "O Over18" para o contexto. Observe que esta declaração de Over18 não revelar qualquer informação sobre a entidade que não seja o fato de que é em 18 anos de idade. Observe que a declaração 'Over18' interpretação depende Noções básicas sobre a semântica dessa declaração. A política de autorização que adicionou a declaração compreende as semânticas em algum nível. Código que subsequentemente examina as declarações que resultam da avaliação de política também ser informado sobre essas semânticas.  
  
 Uma diretiva de autorização determinado pode exigir que ele seja avaliado várias vezes, porque, como outras políticas de autorização adicionar declarações, essa política de autorização pode adicionar ainda mais declarações. Modelo de identidade é projetado para continuar avaliação até que nenhum mais declarações são adicionadas ao contexto de qualquer uma das políticas de autorização em vigor. Essa avaliação contínua de diretivas de autorização impede que o requisito para forçar uma ordem de avaliação específicos em relação a políticas de autorização; eles podem ser avaliados em qualquer ordem. Por exemplo, se a diretiva X apenas adiciona declaração Z se política A adicionou declaração B, em seguida, se X for avaliado primeiro, inicialmente não adiciona Z a declaração. Posteriormente, A é avaliada e adiciona declaração B. X é avaliada uma segunda vez e, desta vez, ele adiciona Z de declaração.  
  
 Um determinado sistema pode ter várias diretivas de autorização em vigor.  
  
### <a name="a-key-making-machine"></a>Um computador de criação de chave  
 Avaliação de um grupo de políticas de autorização associado é como usar uma máquina que torna as chaves. As políticas de autorização são cada avaliada e conjuntos de declarações são gerados, criando a forma da chave. Uma vez concluída a forma da chave, ele pode ser usado para tentar abrir alguns bloqueios. A forma da chave é armazenada em um "contexto de autorização", que é criado por um Gerenciador de autorização.  
  
### <a name="authorization-context"></a>Contexto de autorização  
 Um Gerenciador de autorização avalia as várias políticas de autorização conforme descrito, e o resultado é um contexto de autorização (um conjunto de conjuntos de declarações e algumas propriedades associadas). O contexto de autorização pode ser examinado para determinar quais declarações estão presentes nesse contexto, as relações entre essas várias declarações (por exemplo, o conjunto de declaração de emissão) e, por fim, compare-os com alguns requisitos que eles devem atender para acessar um recurso.  
  
### <a name="locks"></a>Bloqueios  
 Se um contexto de autorização (um conjunto de declarações) é uma chave, os requisitos que devem ser atendidos para conceder acesso a um determinado recurso protegido constituem o bloqueio deve ajustar-se a chave. Modelo de identidade não formalizar como esses requisitos são expressos, mas, considerando a natureza baseada em declarações do sistema, envolvem comparando as declarações no contexto de autorização em relação a um conjunto de declarações necessárias.  
  
### <a name="a-recap"></a>Uma recapitulação  
 Modelo de identidade é baseado em torno do conceito de declarações. Declarações são agrupadas em conjuntos e agregadas em um contexto de autorização. Um contexto de autorização contém um conjunto de declarações e é o resultado da avaliação de uma ou mais políticas de autorização associadas a um Gerenciador de autorização. Essas declaração conjuntos podem ser examinados para determinar se os requisitos de acesso tiverem sido atendidos. A figura a seguir mostra as relações entre esses vários conceitos de modelo de identidade.  
  
 ![Gerenciando reivindicações e autorização](../../../../docs/framework/wcf/feature-details/media/xsi-recap.gif "xsi_recap")  
  
## <a name="wcf-and-identity-model"></a>WCF e o modelo de identidade  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa a infra-estrutura do modelo de identidade como base para a execução de autorização. Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> classe permite que você especifique *autorização* políticas como parte de um serviço. Essas diretivas de autorização são conhecidas como *políticas de autorização externa*, e eles podem executar o processamento de solicitações com base na política local ou interação com um serviço remoto. O Gerenciador de autorização, representado pelo <xref:System.ServiceModel.ServiceAuthorizationManager> classe avalia as políticas de autorização externa junto com as políticas de autorização que reconhecem os vários tipos (tokens) de credenciais e preenche o que é chamado de um  *contexto de autorização* com as declarações apropriadas para uma mensagem de entrada. O contexto de autorização é representado pela <xref:System.IdentityModel.Policy.AuthorizationContext> classe.  
  
## <a name="identity-model-programming"></a>Programação de modelo de identidade  
 A tabela a seguir descreve o modelo de objeto usado para extensões de modelo de identidade do programa. Essas classes todas existirem no <xref:System.IdentityModel.Policy> ou <xref:System.IdentityModel.Claims> namespaces.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|Componente de autorização|Uma classe de modelo de identidade que implementa o <xref:System.IdentityModel.Policy.IAuthorizationComponent> interface.|  
|<xref:System.IdentityModel.Policy.IAuthorizationComponent>|Uma interface que fornece uma propriedade única cadeia de caracteres somente leitura: ID. O valor dessa propriedade é exclusivo para cada instância no sistema que implementa essa interface.|  
|<xref:System.IdentityModel.Policy.AuthorizationContext>|Um *componente de autorização* que contém um conjunto de `ClaimSet` instâncias com zero ou mais propriedades; o resultado da avaliação de uma ou mais políticas de autorização.|  
|<xref:System.IdentityModel.Claims.Claim>|Uma combinação de um tipo de declaração, à direita e um valor. As partes direita e valor são restritas pelo tipo de declaração.|  
|<xref:System.IdentityModel.Claims.ClaimSet>|Uma classe base abstrata. Uma coleção de instâncias `Claim`.|  
|<xref:System.IdentityModel.Claims.DefaultClaimSet>|Uma classe sealed. Uma implementação de `ClaimSet` classe.|  
|<xref:System.IdentityModel.Policy.EvaluationContext>|Uma classe base abstrata. Passado para uma política de autorização durante a avaliação da política.|  
|<xref:System.IdentityModel.Policy.IAuthorizationPolicy>|Uma interface derivada de `IAuthorizationComponent` e implementada pelas classes de política de autorização.|  
|<xref:System.IdentityModel.Claims.Rights>|Uma classe estática que contém valores predefinidos de à direita.|  
  
 As classes a seguir também são usadas para a identidade do modelo de programação, mas não foi encontradas no <xref:System.IdentityModel.Policy> ou <xref:System.IdentityModel.Claims> namespaces.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager>|Uma classe que fornece um método — <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>— executar a autorização baseada em declarações verifica para cada operação em um serviço. Você deve derivar da classe e substituir o método.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>|Uma classe sealed que fornece várias propriedades relacionadas ao comportamento de serviço relacionada à autorização.|  
|<xref:System.ServiceModel.ServiceSecurityContext>|Uma classe que fornece o contexto de segurança, incluindo o contexto de autorização, para em execução (ou prestes a ser executado) operação. Uma instância dessa classe é parte do <xref:System.ServiceModel.OperationContext>.|  
  
### <a name="significant-members"></a>Membros significativos  
 Os seguintes membros são usados para criar novos tipos de declaração.  
  
|Membro|Descrição|  
|------------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>|Classes derivadas implementam este método para executar verificações de acesso baseado em declaração antes de executar operações em um serviço. Todas as informações no fornecido <xref:System.ServiceModel.OperationContext>, ou em outro local, podem ser examinadas ao fazer o acesso a decisão de verificação. Se <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> retorna `true`, acesso e a operação pode ser executado. Se `CheckAccessCore` retorna `false`, o acesso foi negado e a operação não foi executada. Para obter um exemplo, consulte [como: criar um Gerenciador de autorização personalizada para um serviço](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A>|Retorna o <xref:System.ServiceModel.ServiceAuthorizationManager> para o serviço. O <xref:System.ServiceModel.ServiceAuthorizationManager> é responsável para tomar decisões de autorização.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>|A coleção de políticas de autorização personalizada especificada para o serviço. Essas políticas são avaliadas além essas políticas associadas com as credenciais em mensagens de entrada.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Policy.EvaluationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationComponent>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims>  
 <xref:System.IdentityModel.Policy>  
 <xref:System.IdentityModel.Tokens>  
 <xref:System.IdentityModel.Selectors>  
 [Declarações e tokens](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [Declarações e negar acesso a recursos](../../../../docs/framework/wcf/feature-details/claims-and-denying-access-to-resources.md)  
 [Valores de recursos e criação de declarações](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [Como criar uma declaração personalizada](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)  
 [Como comparar declarações](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)  
 [Como criar uma política de autorização personalizada](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-policy.md)  
 [Como criar um gerenciador de autorização personalizado para um serviço](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
