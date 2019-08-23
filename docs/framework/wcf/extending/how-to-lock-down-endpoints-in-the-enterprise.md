---
title: 'Como: bloquear pontos de extremidade na empresa'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: 6a74df56d4c283569988d310b2a501e6440f58ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951651"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Como: bloquear pontos de extremidade na empresa
Grandes empresas geralmente exigem que os aplicativos sejam desenvolvidos em conformidade com as políticas de segurança corporativa. O tópico a seguir discute como desenvolver e instalar um validador de ponto de extremidade do cliente que pode ser usado para validar todos os aplicativos cliente do Windows Communication Foundation (WCF) instalados nos computadores.  
  
 Nesse caso, o validador é um validador de cliente porque esse comportamento de ponto de extremidade é adicionado à seção cliente [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) no arquivo Machine. config. O WCF carrega comportamentos comuns de ponto de extremidade apenas para aplicativos cliente e carrega comportamentos de serviço comuns somente para aplicativos de serviço. Para instalar esse mesmo validador para aplicativos de serviço, o validador deve ser um comportamento de serviço. Para obter mais informações, consulte a seção [ \<> de commonBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) .  
  
> [!IMPORTANT]
> Os comportamentos de serviço ou ponto de extremidade <xref:System.Security.AllowPartiallyTrustedCallersAttribute> não marcados com o atributo (APTCA) que são adicionados [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) à seção de > commonBehaviors de um arquivo de configuração não são executados quando o aplicativo é executado em um ambiente de confiança parcial e não a exceção é lançada quando isso ocorre. Para impor a execução de comportamentos comuns, como validadores, você deve:  
>   
>  --Marque seu comportamento comum com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo para que ele possa ser executado quando implantado como um aplicativo de confiança parcial. Observe que uma entrada de registro pode ser definida no computador para impedir que assemblies marcados com APTCA sejam executados.  
>   
>  --Verifique se o aplicativo é implantado como um aplicativo totalmente confiável que os usuários não podem modificar as configurações de segurança de acesso ao código para executar o aplicativo em um ambiente de confiança parcial. Se puderem fazer isso, o validador personalizado não é executado e nenhuma exceção é gerada. Para obter uma maneira de garantir isso, consulte `levelfinal` a opção usando a [ferramenta de política de segurança de acesso ao código (Caspol. exe)](https://go.microsoft.com/fwlink/?LinkId=248222).  
>   
>  Para obter mais informações, consulte [práticas recomendadas de confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) e [cenários de implantação com suporte](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md).  
  
### <a name="to-create-the-endpoint-validator"></a>Para criar o validador de ponto de extremidade  
  
1. Crie um <xref:System.ServiceModel.Description.IEndpointBehavior> com as etapas de validação desejadas <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> no método. O código a seguir fornece um exemplo. (O `InternetClientValidatorBehavior` é tirado do exemplo de [validação de segurança](../../../../docs/framework/wcf/samples/security-validation.md) .)  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2. Crie um <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> novo que registre o validador de ponto de extremidade criado na etapa 1. O exemplo de código a seguir mostra isso. (O código original para este exemplo está no exemplo de [validação de segurança](../../../../docs/framework/wcf/samples/security-validation.md) .)  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3. Verifique se o assembly compilado está assinado com um nome forte. Para obter detalhes, consulte a [ferramenta Strong Name (SN. EXE)](https://go.microsoft.com/fwlink/?LinkId=248217) e os comandos do compilador para seu idioma.  
  
### <a name="to-install-the-validator-into-the-target-computer"></a>Para instalar o validador no computador de destino  
  
1. Instale o validador de ponto de extremidade usando o mecanismo apropriado. Em uma empresa, isso pode ser usando Política de Grupo e o SMS (Systems Management Server).  
  
2. Instale o assembly de nome forte no cache de assembly global usando o [Gacutil. exe (ferramenta de cache de assembly global)](../../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
3. Use os <xref:System.Configuration?displayProperty=nameWithType> tipos de namespace para:  
  
    1. Adicione a extensão à seção de [ \<> behaviorExtensions](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md) usando um nome de tipo totalmente qualificado e bloqueie o elemento.  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2. Adicione o elemento Behavior à `EndpointBehaviors` propriedade [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) da seção > de commonBehaviors e bloqueie o elemento. (Para instalar o validador no serviço, o validador deve ser <xref:System.ServiceModel.Description.IServiceBehavior> um e adicionado `ServiceBehaviors` à propriedade.) O exemplo de código a seguir mostra a configuração apropriada após as etapas a. e b., com a única exceção de que não há um nome forte.  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3. Salve o arquivo machine.config. O exemplo de código a seguir executa todas as tarefas na etapa 3, mas salva localmente uma cópia do arquivo Machine. config modificado.  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como adicionar um comportamento comum ao arquivo Machine. config e salvar uma cópia no disco. O `InternetClientValidatorBehavior` é tirado do exemplo de [validação de segurança](../../../../docs/framework/wcf/samples/security-validation.md) .  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Você também pode querer criptografar os elementos do arquivo de configuração. Para obter mais informações, consulte a seção Consulte também.  
  
## <a name="see-also"></a>Consulte também

- [Criptografando elementos do arquivo de configuração usando DPAPI](https://go.microsoft.com/fwlink/?LinkId=94954)
- [Criptografando elementos do arquivo de configuração usando RSA](https://go.microsoft.com/fwlink/?LinkId=94955)
