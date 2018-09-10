---
title: Guia de implantação do .NET Framework para administradores
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f56ccbf549ce8f1750ba0bf9cf4a945007694258
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502360"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>Guia de implantação do .NET Framework para administradores
Este artigo passo a passo descreve como um administrador de sistemas pode implantar o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e suas dependências de sistema pela rede usando o Microsoft System Center Configuration Manager. Este artigo pressupõe que todos os computadores clientes de destino atendem aos requisitos mínimos do .NET Framework. Para obter uma lista dos requisitos de hardware e software para instalar o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], consulte [Requisitos do sistema](../../../docs/framework/get-started/system-requirements.md).  
  
> [!NOTE]
>  O software referenciado neste documento, incluindo, sem restrição, o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager e o Active Directory, estão sujeitos aos termos de licença e condições. Essas instruções assumem que esses termos de licença e condições foram examinados e aceitos pelos licenciados apropriados do software. Essas instruções não renunciam nenhum dos termos e condições dos contratos de tal licença.  
>   
>  Para saber mais sobre suporte ao .NET Framework, confira [Política de ciclo de vida de suporte do Microsoft .NET Framework](https://go.microsoft.com/fwlink/?LinkId=196607) no site de Suporte da Microsoft.  
  
 Esse tópico contém as seguintes seções:  
  
 [O processo de implantação](#the_deployment_process)  
 [Implantando o .NET Framework](#deploying_in_a_test_environment)  
 [Criar uma coleção](#creating_a_collection)  
 [Criar um pacote e um programa](#creating_a_package)  
 [Selecionar um ponto de distribuição](#select_dist_point)  
 [Implantar o pacote](#deploying_package)  
[Recursos](#resources)  
[Solução de problemas](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a>O processo de implantação  
 Quando a infraestrutura de suporte estiver disponível, use o System Center 2012 Configuration Manager para implantar o pacote .NET Framework redistribuível em computadores na rede. Estabelecer uma infraestrutura envolve criar e definir cinco áreas principais: coleções, um pacote e programa para o software, pontos de distribuição e implantações.  
  
-   **Coleções** são grupos de recursos do Configuration Manager, como usuários, grupos de usuários ou computadores, nos quais o .NET Framework é implantado. Para obter mais informações, consulte [Coleções no Configuration Manager](https://technet.microsoft.com/library/gg682169.aspx) na biblioteca de documentação do Configuration Manager.  
  
-   **Pacotes e programas** geralmente representam aplicativos de software a serem instalados em um computador cliente, mas também podem conter arquivos individuais, atualizações ou até mesmo comandos individuais. Para obter mais informações, consulte [Pacotes e programas no Configuration Manager](https://technet.microsoft.com/library/gg699369.aspx) na biblioteca de documentação do Configuration Manager.  
  
-   **Pontos de distribuição** são funções do sistema de sites do Configuration Manager que armazenam os arquivos necessários para que o software seja executado em computadores cliente. Quando o cliente do Configuration Manager recebe e processa uma implantação de software, ele contata um ponto de distribuição para baixar o conteúdo associado ao software e iniciar o processo de instalação. Para obter mais informações, consulte [Introdução ao gerenciamento de conteúdo no Configuration Manager](https://technet.microsoft.com/library/gg682083.aspx) na biblioteca de documentação do Configuration Manager.  
  
-   **Implantações** instruem os membros aplicáveis da coleção de destino especificada a instalarem o pacote de software. Para obter mais informações, consulte [Como implantar aplicativos no Configuration Manager](https://technet.microsoft.com/library/gg682082.aspx) na biblioteca de documentação do Configuration Manager.  
  
> [!IMPORTANT]
>  Os procedimentos neste tópico contém configurações comuns para criar e implantar um pacote e um programa e podem não abranger todas as configurações possíveis. Para obter outras opções de implantação do Configuration Manager, consulte a [Biblioteca de documentação do Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx).  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a>Implantando o .NET Framework  
 Você pode usar o System Center 2012 Configuration Manager para implantar uma instalação silenciosa do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], onde os usuários não interagem com o processo de instalação. Siga estas etapas:  
  
1.  [Crie uma coleção](#creating_a_collection).  
  
2.  [Crie um pacote e um programa para o .NET Framework redistribuível](#creating_a_package).  
  
3.  [Selecione um ponto de distribuição](#select_dist_point).  
  
4.  [Implante o pacote](#deploying_package).  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a>Crie uma coleção  
 Nesta etapa, você selecionará os computadores nos quais pacote e o programa serão implantados e os agrupará em uma coleção de dispositivos. Para criar uma coleção no Configuration Manager, você pode usar regras de associação diretas (onde você especifica manualmente os membros da coleção) ou regras de consulta (onde o Configuration Manager determina os membros da coleção com base em critérios especificados). Para obter mais informações sobre regras de associação, inclusive regras diretas e de consulta, consulte [Introdução às coleções no Configuration Manager](https://technet.microsoft.com/library/gg682177.aspx) na biblioteca de documentação do Configuration Manager.  
  
 Para criar uma coleção:  
  
1.  No console do Configuration Manager, escolha **Ativos e Conformidade**.  
  
2.  No espaço de trabalho **Ativos e Conformidade**, escolha **Coleções de Dispositivos**.  
  
3.  Na guia **Início** do grupo **Criar**, escolha **Criar Coleção de Dispositivos**.  
  
4.  Na página **Geral** do **Assistente de Criação de Coleção de Dispositivos**, insira um nome para a coleção.  
  
5.  Escolha **Procurar** para especificar uma coleção de restrição.  
  
6.  Na página **Regras de Associação**, escolha **Adicionar Regra** e escolha **Regra Direta** para abrir o **Assistente de Criação de Regra de Associação Direta**. Escolha **Avançar**.  
  
7.  Na página **Pesquisar Recursos**, na lista **Classe de recurso**, escolha **Recurso do Sistema**. Na lista **Nome do atributo**, escolha **Nome**. No campo **Valor**, insira `%` e escolha **Avançar**.  
  
8.  Na página **Selecionar Recursos**, marque a caixa de seleção para cada computador no qual você deseja implantar o .NET Framework. Escolha **Avançar** e conclua o assistente.  
  
9. Na página **Regras de Associação** do **Assistente de Criação de Coleção de Dispositivos**, escolha **Avançar** e conclua o assistente.  
  
 Para obter mais informações sobre coleções, consulte [Coleções no Configuration Manager](https://technet.microsoft.com/library/bb693730.aspx) na biblioteca de documentação do Configuration Manager.  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>Crie um pacote e programa para o pacote .NET Framework redistribuível  
 As etapas a seguir criam, manualmente, um pacote para o .NET Framework redistribuível. O pacote conterá os parâmetros especificados para instalar o .NET Framework e o local de onde o pacote será distribuído para os computadores de destino.  
  
 Para criar um pacote:  
  
1.  No console do Configuration Manager, escolha **Biblioteca de Software**.  
  
2.  No espaço de trabalho **Biblioteca de Software**, expanda **Gerenciamento de Aplicativos** e escolha **Pacotes**.  
  
3.  Na guia **Início**, no grupo **Criar**, escolha **Criar Pacote**.  
  
4.  Na página **Pacote** do **Assistente para Criar Pacote e Programa**, insira as seguintes informações:  
  
    -   Nome: `.NET Framework 4.5`  
  
    -   Fabricante: `Microsoft`  
  
    -   Idioma. `English (US)`  
  
5.  Escolha **Este pacote contém arquivos de origem** e **Procurar** para selecionar a pasta de rede ou local que contém os arquivos de instalação do .NET Framework. Após selecionar a pasta, escolha **OK** e **Avançar**.  
  
6.  Na página **Tipo de Programa** do assistente, escolha **Programa Padrão** e **Avançar**.  
  
7.  Na página **Programa** do **Assistente para Criar Pacote e Programa**, insira as seguintes informações:  
  
    1.  **Nome:** `.NET Framework 4.5`  
  
    2.  **Linha de comando:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (as opções de linha de comando são descritas na tabela após estas etapas)  
  
    3.  **Executar:** escolha **Oculto**.  
  
    4.  **O programa pode ser executado:** escolha a opção que especifica que o programa pode ser executado independentemente de um usuário estar conectado.  
  
8.  Na página **Requisitos**, escolha **Avançar** para aceitar os valores padrão e conclua o assistente.  
  
 A tabela a seguir descreve as opções de linha de comando especificadas na etapa 7.  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/q**|Define o modo silencioso. Nenhuma entrada do usuário é necessária e nenhuma saída é mostrada.|  
|**/norestart**|Impede que o programa de instalação reinicialize automaticamente. Se você usar essa opção, o Configuration Manager deverá processar a reinicialização do computador.|  
|**/chainingpackage** *PackageName*|Especifica o nome do pacote que está fazendo o encadeamento. Essa informação é relatada com outras informações da sessão de instalação para aqueles que se inscreveram no [Programa de Aperfeiçoamento da Experiência do Usuário da Microsoft (CEIP)](https://go.microsoft.com/fwlink/p/?LinkId=248244). Se o nome do pacote contiver espaços, use aspas duplas como delimitadores: **/chainingpackage "Chaining Product"**.|  
  
 Estas etapas criam um pacote chamado .NET Framework 4.5. O programa implanta uma instalação silenciosa do .NET Framework 4.5. Em uma instalação silenciosa, os usuários não interagem com o processo de instalação e o aplicativo de encadeamento precisa capturar o código de retorno e manipular a reinicialização; consulte [Obtendo informações de progresso de um pacote de instalação](https://go.microsoft.com/fwlink/?LinkId=179606).  
 
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a>Selecione um ponto de distribuição  
 Para distribuir o pacote e o programa para computadores clientes de um servidor, primeiro designe um sistema de site como um ponto de distribuição e distribua o pacote para o ponto de distribuição.  
  
 Use as etapas a seguir para selecionar um ponto de distribuição para o pacote .NET Framework 4.5 criado na seção anterior:  
  
1.  No console do Configuration Manager, escolha **Biblioteca de Software**.  
  
2.  No espaço de trabalho **Biblioteca de Software**, expanda **Gerenciamento de Aplicativos** e escolha **Pacotes**.  
  
3.  Na lista de pacotes, selecione o pacote **.NET Framework 4.5** que você criou na seção anterior.  
  
4.  Na guia **Início** do grupo **Implantação**, escolha **Distribuir Conteúdo**.  
  
5.  Na guia **Geral** do **Assistente para Distribuir Conteúdo**, escolha **Avançar**.  
  
6.  Na página **Destino de Conteúdo** do assistente, escolha **Adicionar** e **Ponto de Distribuição**.  
  
7.  Na caixa de diálogo **Adicionar Pontos de Distribuição**, selecione os pontos de distribuição que hospedarão o pacote e o programa e escolha **OK**.  
  
8.  Conclua o assistente.  
  
 O pacote agora conterá todas as informações que você precisa para implantar silenciosamente o .NET Framework 4.5. Antes de você implantar o pacote e o programa, verifique se ele foi instalado no ponto de distribuição, consulte a seção "Monitorar conteúdo" em [Operações e manutenção para o gerenciamento de conteúdo no Configuration Manager](https://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) na biblioteca de documentação do Configuration Manager.  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a>Implante o pacote  
 Para implantar o pacote e o programa .NET Framework 4.5:  
  
1.  No console do Configuration Manager, escolha **Biblioteca de Software**.  
  
2.  No espaço de trabalho **Biblioteca de Software**, expanda **Gerenciamento de Aplicativos** e escolha **Pacotes**.  
  
3.  Na lista de pacotes, selecione o pacote criado e denominado **.NET Framework 4.5**.  
  
4.  Na guia **Início**, no grupo **Implantação**, escolha **Implantar**.  
  
5.  Na página **Geral** do **Assistente de Implantação de Software**, escolha **Procurar** e selecione a coleção anteriormente criada. Escolha **Avançar**.  
  
6.  Na página **Conteúdo** do assistente, verifique se o ponto do qual você deseja distribuir o software é exibido e escolha **Avançar**.  
  
7.  Na página **Configurações de Implantação** do assistente, confirme se a **Ação** está definida como **Instalar** e a **Finalidade** como **Obrigatório**. Isso garantirá que o pacote de software seja uma instalação obrigatória nos computadores de destino. Escolha **Avançar**.  
  
8.  Na página **Agendamento** do assistente, especifique quando você deseja que o .NET Framework seja instalado. Você pode escolher **Nova** para atribuir uma hora de instalação ou instruir o software a ser instalado quando o usuário fizer logon, logoff ou assim que possível. Escolha **Avançar**.  
  
9. Na página **Experiência do Usuário** do assistente, use os valores padrão e escolha **Avançar**.  
  
    > [!WARNING]
    >  O ambiente de produção pode ter políticas que exijam diferentes seleções de agendamento de implantação. Para obter informações sobre essas opções, consulte [Propriedades de nome de anúncio: guia Agendamento](https://technet.microsoft.com/library/bb694016.aspx) na Biblioteca TechNet.  
  
10. Na página **Pontos de Distribuição** do assistente, use os valores padrão e escolha **Avançar**.  
  
11. Conclua o assistente. Você pode monitorar o progresso da implantação no nó **Implantações** do espaço de trabalho **Monitoramento**.  
  
 O pacote agora será implantado na coleção de destino e a instalação silenciosa do .NET Framework 4.5 será iniciada. Para obter informações sobre códigos de erro de instalação do .NET Framework 4.5, consulte a seção [Códigos de retorno](#return_codes) posteriormente neste tópico.  
  
<a name="resources"></a>   
## <a name="resources"></a>Recursos  
 Para obter mais informações sobre a infraestrutura para testar a implantação do pacote [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistribuível, consulte os recursos a seguir.  
  
 **Active Directory, DNS, DHCP:**  
  
-   [Active Directory Domain Services para Windows Server 2008](https://technet.microsoft.com/library/dd378891.aspx)  
  
-   [Servidor DNS](https://technet.microsoft.com/library/cc732997.aspx)  
  
-   [Servidor DHCP](https://technet.microsoft.com/library/cc896553.aspx)  
  
 **SQL Server 2008:**  
  
-   [Instalando o SQL Server 2008 (vídeo do SQL Server)](https://technet.microsoft.com/library/dd299415.aspx)  
  
-   [Visão geral de segurança do SQL Server 2008 para administradores de banco de dados](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 **System Center 2012 Configuration Manager (Ponto de Gerenciamento, Ponto de Distribuição):**  
  
-   [Administração de site do System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg681983.aspx)  
  
-   [Planejando e implantando site único do Configuration Manager](https://technet.microsoft.com/library/bb680961.aspx)  
  
 **Cliente do System Center 2012 Configuration Manager para computadores Windows:**  
  
-   [Implantação de clientes do System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg699391.aspx)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a>Solução de problemas  
  
### <a name="log-file-locations"></a>Localizações dos arquivos de log  
 Os seguintes arquivos de log são gerados durante a configuração do .NET Framework:  
  
 %temp%\Microsoft .NET Framework *versão*\*.txt  
 %temp%\Microsoft .NET Framework *versão*\*.html  
  
 em que *versão* é a versão do .NET Framework que você está instalando, como 4.5 ou 4.7.2.  
 
 Também é possível especificar o diretório no qual os arquivos de log são gravados usando a opção de linha de comando `/log` no comando de instalação do .NET Framework. Para obter mais informações, consulte [Guia de implantação do .NET Framework para desenvolvedores](deployment-guide-for-developers.md#command-line-options). 
 
 Você pode usar a [ferramenta de coleta de logs](https://www.microsoft.com/download/details.aspx?id=12493) para coletar os arquivos de log do .NET Framework e criar um arquivo de gabinete compactado (.cab) que reduz o tamanho dos arquivos.  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a>Códigos de retorno  
 A tabela a seguir lista os códigos de retorno mais comuns do programa de instalação do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistribuível. Os códigos de retorno são os mesmos para todas as versões do instalador.  
  
 Para obter links para informações detalhadas, consulte a próxima seção [Códigos de erro de download](#additional_error_codes).  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|0|A instalação foi concluída com êxito.|  
|1602|O usuário cancelou a instalação.|  
|1603|Ocorreu um erro fatal durante a instalação.|  
|1641|É necessário reiniciar para concluir a instalação. Esta mensagem indica êxito.|  
|3010|É necessário reiniciar para concluir a instalação. Esta mensagem indica êxito.|  
|5100|O computador do usuário não atende aos requisitos do sistema.|  
  
<a name="additional_error_codes"></a>   
### <a name="download-error-codes"></a>Códigos de erro de download  
  
-   [Códigos de erro do BITS (Serviço de Transferência Inteligente em Segundo Plano)](https://msdn.microsoft.com/library/aa362823.aspx)  
  
-   [Códigos de erro do moniker de URL](https://msdn.microsoft.com/library/ms775145.aspx)  
  
-   [Códigos de erro WinHttp](/windows/desktop/WinHttp/error-messages)  
  
 Outros códigos de erro:  
  
-   [Códigos de erro do Windows Installer](https://msdn.microsoft.com/library/aa368542.aspx)  
  
-   [Códigos de resultado do Windows Update Agent](https://technet.microsoft.com/library/cc720442.aspx)  
  
## <a name="see-also"></a>Consulte também  
 [Guia de implantação para desenvolvedores](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Requisitos do sistema](../../../docs/framework/get-started/system-requirements.md)
