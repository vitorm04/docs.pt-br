---
title: Como bloquear pontos de extremidade na empresa
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: 032b69c1fae38576b0374b329f1ab6fe90e2b1a0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43806193"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Como bloquear pontos de extremidade na empresa
Empresas de grandes porte geralmente exigem que os aplicativos são desenvolvidos em conformidade com políticas de segurança da empresa. O tópico a seguir discute como desenvolver e instalar um validador de ponto de extremidade do cliente que pode ser usado para validar todos os aplicativos de cliente do Windows Communication Foundation (WCF) instalados em computadores.  
  
 Nesse caso, o validador é um validador de cliente, pois esse comportamento de ponto de extremidade é adicionado ao cliente [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) seção no arquivo Machine. config. WCF carrega comportamentos de ponto de extremidade comuns somente para aplicativos cliente e carrega os comportamentos de serviço comuns apenas para aplicativos de serviço. Para instalar esse validador mesmo para aplicativos de serviço, o validador deve ser um comportamento de serviço. Para obter mais informações, consulte o [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) seção.  
  
> [!IMPORTANT]
>  Comportamentos de serviço ou ponto de extremidade não marcado com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) que são adicionados para o [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) seção de um arquivo de configuração não são executados quando o aplicativo é executado em uma relação de confiança parcial ambiente e nenhuma exceção é lançada quando isso ocorre. Para impor a execução de comportamentos comuns, como validadores, você deve:  
>   
>  – Marcar seu comportamento comum com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> de atributo para que ele possa executar quando implantado como um aplicativo de confiança parcial. Observe que uma entrada de registro pode ser definida no computador para impedir que os assemblies marcados com APTCA em execução...  
>   
>  – Verifique se o aplicativo é implantado como um aplicativo totalmente confiável que os usuários não podem modificar as configurações de segurança de acesso ao código para executar o aplicativo em um ambiente de confiança parcial. Se eles podem fazer isso, o validador personalizado não é executado e nenhuma exceção é lançada. Para uma forma de garantir isso, consulte a `levelfinal` usando a opção [ferramenta de política de segurança de acesso de código (Caspol.exe)](https://go.microsoft.com/fwlink/?LinkId=248222).  
>   
>  Para obter mais informações, consulte [práticas recomendadas de confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) e [suporte para cenários de implantação](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md).  
  
### <a name="to-create-the-endpoint-validator"></a>Para criar o validador de ponto de extremidade  
  
1.  Criar uma <xref:System.ServiceModel.Description.IEndpointBehavior> com as etapas de validação desejada no <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> método. O código a seguir fornece um exemplo. (O `InternetClientValidatorBehavior` é obtida a [validação de segurança](../../../../docs/framework/wcf/samples/security-validation.md) exemplo.)  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2.  Criar um novo <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> que registra o validador de ponto de extremidade criado na etapa 1. O exemplo de código a seguir mostra isso. (O código original para este exemplo está no [validação de segurança](../../../../docs/framework/wcf/samples/security-validation.md) exemplo.)  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3.  Verifique se que o assembly compilado é assinado com um nome forte. Para obter detalhes, consulte o [ferramenta de nome forte (SN. EXE)](https://go.microsoft.com/fwlink/?LinkId=248217) e os comandos do compilador para seu idioma.  
  
### <a name="to-install-the-validator-into-the-target-computer"></a>Para instalar o validador para o computador de destino  
  
1.  Instale o validador de ponto de extremidade usando o mecanismo apropriado. Em uma empresa, isso pode estar usando diretiva de grupo e o Systems Management Server (SMS).  
  
2.  Instalar o assembly de nome forte no cache de assembly global usando o [Gacutil.exe (ferramenta de Cache de Assembly Global)](https://msdn.microsoft.com/library/ex0ss12c\(v=vs.110\).aspx).  
  
3.  Use o <xref:System.Configuration?displayProperty=nameWithType> tipos de namespace:  
  
    1.  Adicionar a extensão para o [ \<behaviorExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md) seção usando um nome de tipo totalmente qualificado e o elemento de bloqueio.  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2.  Adicione o elemento de comportamento para o `EndpointBehaviors` propriedade do [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) seção e bloquear o elemento. (Para instalar o validador no serviço, o validador deve ser um <xref:System.ServiceModel.Description.IServiceBehavior> e adicionado ao `ServiceBehaviors` propriedade.) O exemplo de código a seguir mostra a configuração adequada após etapas um. e b., com exceção que não há nenhum nome forte.  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3.  Salve o arquivo machine.config. O exemplo de código a seguir executa todas as tarefas na etapa 3, mas salva uma cópia do arquivo Machine. config modificado localmente.  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como adicionar um comportamento comum para o arquivo Machine. config e salvar uma cópia em disco. O `InternetClientValidatorBehavior` é obtida a [validação de segurança](../../../../docs/framework/wcf/samples/security-validation.md) exemplo.  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Talvez você queira criptografar os elementos do arquivo de configuração. Para obter mais informações, consulte a seção Consulte também.  
  
## <a name="see-also"></a>Consulte também  
 [Criptografia de elementos do arquivo de configuração usando a DPAPI](https://go.microsoft.com/fwlink/?LinkId=94954)  
 [Criptografia de elementos do arquivo de configuração usando o RSA](https://go.microsoft.com/fwlink/?LinkId=94955)
