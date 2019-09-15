---
title: Visão geral da Segurança do Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- code access security [Windows Forms], Windows Forms
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms], about security
- access control [Windows Forms], Windows Forms
ms.assetid: 4810dc9f-ea23-4ce1-8ea1-657f0ff1d820
ms.openlocfilehash: 08c80eccee395d9141978a7d4594205af1a51ed9
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972128"
---
# <a name="security-in-windows-forms-overview"></a>Visão geral da Segurança do Windows Forms

Antes do lançamento da .NET Framework, todo o código em execução no computador de um usuário tinha os mesmos direitos ou permissões para acessar os recursos que um usuário do computador tinha. Por exemplo, se o usuário era autorizado a acessar o sistema de arquivos, o código era autorizado a acessar o sistema de arquivos. Se o usuário era autorizado a acessar um banco de dados, o código era autorizado a acessar o banco de dados. Embora esses direitos ou permissões possam ser aceitáveis para código em executáveis que o usuário explicitamente instalou no computador local, eles podem não ser aceitáveis para código potencialmente mal-intencionado proveniente da Internet ou de uma intranet local. Esse código não deveria ser capaz de acessar recursos do computador do usuário sem permissão.

O .NET Framework introduz uma infraestrutura chamada segurança de acesso ao código que permite diferenciar as permissões, ou direitos, que o código tem dos direitos que o usuário tem. Por padrão, o código proveniente da Internet e da intranet somente pode executar no que é conhecido como confiança parcial. A confiança parcial sujeita um aplicativo a uma série de restrições: entre outras coisas, um aplicativo é impedido de acessar o disco rígido local e não pode executar código não gerenciado. O .NET Framework controla os recursos que o código tem permissão para acessar com base na identidade desse código: de onde ele veio, se ele tem um [assembly de nome forte](../../standard/assembly/strong-named.md), se ele está assinado com um certificado e assim por diante.

A tecnologia ClickOnce, que você usa para implantar Windows Forms aplicativos, ajuda a facilitar o desenvolvimento de aplicativos que são executados em confiança parcial, com confiança total ou em confiança parcial com permissões elevadas. O ClickOnce fornece recursos como elevação de permissão e implantação de aplicativo confiável para que seu aplicativo possa solicitar confiança total ou permissões elevadas do usuário local de uma maneira responsável.

## <a name="understanding-security-in-the-net-framework"></a>Noções básicas sobre segurança no .NET Framework

A segurança de acesso do código permite que o código seja confiável em graus variáveis, dependendo da origem do código e de outros aspectos de sua identidade. Para obter mais informações sobre a evidência que o Common Language Runtime usa para determinar a política de segurança, consulte [Evidências](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd(v=vs.100)). Ele ajuda a proteger os sistemas do computador contra código mal-intencionado e ajuda a proteger o código confiável contra intencionalmente ou acidentalmente comprometer a segurança. A segurança de acesso do código também oferece mais controle sobre quais ações seu aplicativo pode realizar, porque você pode especificar somente as permissões que você precisa que seu aplicativo tenha. A segurança de acesso do código afeta todo código gerenciado que se destina ao Common Language Runtime, mesmo que esse código não faça nenhuma verificação de permissão de segurança de acesso do código. Para obter mais informações sobre segurança na .NET Framework, consulte [conceitos principais de segurança](../../standard/security/key-security-concepts.md) e [noções básicas de segurança de acesso ao código](../misc/code-access-security-basics.md).

Se o usuário executar um arquivo executável dos Windows Forms diretamente de um servidor Web ou de um compartilhamento de arquivos, o grau de confiança concedido ao seu aplicativo dependerá de onde reside o código e de como ele foi iniciado. Quando um aplicativo é executado, ele é automaticamente avaliado e recebe um conjunto de permissões nomeadas do Common Language Runtime. Por padrão, o conjunto de permissões de Confiança Total é concedido ao código do computador local, o conjunto de permissões de Intranet Local é concedido ao código de uma rede local e o conjunto de permissões de Internet é concedido ao código da Internet.

> [!NOTE]
> No .NET Framework versão 1,0 Service Pack 1 e Service Pack 2, o grupo de códigos de zona da Internet recebe o conjunto de permissões Nothing. Em todas as outras versões do .NET Framework, o grupo de códigos de zona da Internet recebe as permissões da Internet definidas.
>
> As permissões padrão concedidas em cada um desses conjuntos de permissão são listadas no tópico [Política de segurança padrão](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100)). Dependendo das permissões que o aplicativo recebe, ele é executado corretamente ou gera uma exceção de segurança.
>
> Muitos aplicativos Windows Forms serão implantados usando o ClickOnce. As ferramentas usadas para gerar uma implantação do ClickOnce têm padrões de segurança diferentes do que o que foi discutido anteriormente. Para obter mais informações, veja a seguinte discussão.

As permissões reais concedidas ao seu aplicativo podem ser diferentes dos valores padrão, porque a política de segurança pode ser modificada. Isso significa que seu aplicativo pode ter permissão em um computador, mas não em outro.

## <a name="developing-a-more-secure-windows-forms-application"></a>Desenvolvendo um aplicativo mais seguro dos Windows Forms

A segurança é importante em todas as etapas do desenvolvimento de aplicativos. Comece revisando e seguindo as [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md).

Em seguida, decida se seu aplicativo deve ser executado em confiança total ou em confiança parcial. Executar o aplicativo em confiança total facilita o acesso a recursos no computador local, mas expõe seu aplicativo e os usuários a altos riscos de segurança, caso você não crie e desenvolva seu aplicativo estritamente de acordo com o tópico Diretrizes de codificação segura. Executar o aplicativo em confiança parcial facilita o desenvolvimento de um aplicativo mais seguro e reduz muito o risco, mas exige mais planejamento sobre como implementar determinados recursos.

Se você escolher a confiança parcial (isto é, os conjuntos de permissões de Internet ou de Intranet Local), decida como deseja que o aplicativo se comporte nesse ambiente. O Windows Forms fornece maneiras alternativas e mais seguras para implementar recursos quando em um ambiente semi-confiável. Certas partes do seu aplicativo, como o acesso a dados, podem ser projetadas e escritas de maneiras diferentes para ambientes de confiança total e de confiança parcial. Alguns recursos dos Windows Forms, como as configurações de aplicativo, são projetados para funcionar em confiança parcial. Para obter mais informações, consulte [Visão geral de configurações de aplicativo](./advanced/application-settings-overview.md).

Se seu aplicativo precisa de mais permissões que as concedidas pela confiança parcial, mas você não deseja executar em confiança total, você pode executar em confiança parcial, declarando somente as permissões adicionais que são necessárias. Por exemplo, se você deseja executar com confiança parcial, mas deve conceder a seu aplicativo acesso somente leitura a um diretório no sistema de arquivos do usuário, você pode solicitar <xref:System.Security.Permissions.FileIOPermission> somente para esse diretório. Se for usada corretamente, essa abordagem pode fornecer funcionalidade aumentada ao seu aplicativo e minimizar os riscos de segurança para seus usuários.

Ao desenvolver um aplicativo que será executado em confiança parcial, mantenha o controle sobre quais permissões seu aplicativo deve executar e quais permissões seu aplicativo pode usar opcionalmente. Quando todas as permissões forem conhecidas, você deverá fazer uma solicitação declarativa de permissão no nível do aplicativo. A solicitação de permissões informa o .NET Framework tempo de execução sobre quais permissões seu aplicativo precisa e quais permissões ele não deseja especificamente. Para obter mais informações sobre a solicitação de permissões, consulte [Solicitando permissões](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100)).

Ao solicitar permissões opcionais, você deverá tratar as exceções de segurança que serão geradas se o aplicativo realizar uma ação que exija permissões que não foram concedidas a ele. A manipulação apropriada do <xref:System.Security.SecurityException> garantirá que seu aplicativo possa continuar a operar. Seu aplicativo pode usar a exceção para determinar se um recurso deve ser desabilitado para o usuário. Por exemplo, um aplicativo poderá desabilitar a opção de menu **Salvar** se a permissão de arquivo necessária não for concedida.

Às vezes é difícil saber se você declarou todas as permissões apropriadas. Uma chamada de método que parece inofensiva na superfície, por exemplo, pode acessar o sistema de arquivos em algum ponto durante sua execução. Se você não implantar seu aplicativo com todas as permissões necessárias, poderá ser bem sucedido em teste, quando você depurá-lo na área de trabalho, mas falhar ao ser implantado. O SDK .NET Framework 2,0 e o Visual Studio 2005 contêm ferramentas para calcular as permissões que um aplicativo precisa: a ferramenta de linha de comando MT. exe e o recurso Calculate Permissions do Visual Studio, respectivamente.

Os tópicos a seguir descrevem recursos adicionais de segurança dos Windows Forms.

|Tópico|Descrição|
|-----------|-----------------|
|- [Acesso mais seguro a arquivos e a dados nos Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)|Descreve como acessar arquivos e dados em um ambiente de confiança parcial.|
|- [Impressão mais segura nos Windows Forms](more-secure-printing-in-windows-forms.md)|Descreve como acessar os recursos de impressão em um ambiente de confiança parcial.|
|- [Considerações adicionais sobre segurança nos Windows Forms](additional-security-considerations-in-windows-forms.md)|Descreve como realizar manipulação de janela, como usar a área de transferência e como fazer chamadas a código não gerenciado em um ambiente de confiança parcial.|

### <a name="deploying-an-application-with-the-appropriate-permissions"></a>Implantando um aplicativo com as permissões apropriadas

O meio mais comum de implantar um aplicativo Windows Forms em um computador cliente é com o ClickOnce, uma tecnologia de implantação que descreve todos os componentes que seu aplicativo precisa executar. O ClickOnce usa arquivos XML chamados manifestos para descrever os assemblies e arquivos que compõem seu aplicativo e também as permissões que seu aplicativo requer.

O ClickOnce tem duas tecnologias para solicitar permissões elevadas em um computador cliente. As duas tecnologias contam com o uso de certificados Authenticode. Os certificados ajudam a fornecer alguma garantia para os usuários de que o aplicativo é proveniente de uma fonte confiável.

A tabela a seguir descreve essas tecnologias.

|Tecnologia de permissões elevadas|Descrição|
|------------------------------------|-----------------|
|Elevação de permissões|Exibe ao usuário uma caixa de diálogo de segurança na primeira vez que seu aplicativo é executado. A caixa de diálogo de **Elevação de permissões** informa ao usuário sobre quem publicou o aplicativo, para que o usuário possa tomar uma decisão informada sobre se deve conceder confiança adicional|
|Implantação de aplicativo confiável|Envolve um administrador do sistema realizando a instalação de um certificado Authenticode de editor em um computador cliente uma única vez. Daí em diante, todos os aplicativos assinados com o certificado serão considerados confiáveis e poderão ser executados em confiança total no computador local, sem avisos adicionais.|

A tecnologia escolhida dependerá de seu ambiente de implantação. Para obter mais informações, consulte [Escolhendo uma estratégia de implantação do ClickOnce](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).

Por padrão, os aplicativos ClickOnce implantados usando o Visual Studio ou as ferramentas SDK do .NET Framework (Mage. exe e MageUI. exe) são configurados para serem executados em um computador cliente com confiança total. Se você estiver implantando seu aplicativo usando a confiança parcial ou usando somente algumas permissões adicionais, você terá que alterar esse padrão. Isso pode ser feito com o Visual Studio ou com a ferramenta SDK do .NET Framework MageUI. exe quando você configura a implantação. Para obter mais informações sobre como usar o MageUI. exe, [consulte Passo a passos: Implantando manualmente um aplicativo](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)ClickOnce.  Consulte [também como: Defina permissões personalizadas para um aplicativo](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hafybdaa(v=vs.110)) ClickOnce ou [como: Defina permissões personalizadas para um aplicativo](/visualstudio/deployment/how-to-set-custom-permissions-for-a-clickonce-application)ClickOnce.

Para obter mais informações sobre os aspectos de segurança do ClickOnce e a elevação de permissões, consulte [Securing ClickOnce Applications](/visualstudio/deployment/securing-clickonce-applications). Para obter mais informações sobre a implantação de aplicativo confiável, consulte [Visão geral da implantação de aplicativos confiáveis](/visualstudio/deployment/trusted-application-deployment-overview).

### <a name="testing-the-application"></a>Testando o aplicativo

Se você tiver implantado seu aplicativo Windows Forms usando o Visual Studio, poderá habilitar a depuração em confiança parcial ou um conjunto de permissões restritos do ambiente de desenvolvimento.  Consulte [também como: Depurar um aplicativo ClickOnce com permissões restritas](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions).

## <a name="see-also"></a>Consulte também

- [Segurança do Windows Forms](windows-forms-security.md)
- [Noções Básicas da Segurança de Acesso do Código](../misc/code-access-security-basics.md)
- [Segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Visão geral da implantação de aplicativos confiáveis](/visualstudio/deployment/trusted-application-deployment-overview)
- [Mage.exe (Manifest Generation and Editing Tool)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (Manifest Generation and Editing Tool, cliente gráfico)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
