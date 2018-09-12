---
title: Executando os exemplos do Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: d6fc93af217bfc282ce7030973be32baf7d864cd
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44510149"
---
# <a name="running-the-windows-communication-foundation-samples"></a>Executando os exemplos do Windows Communication Foundation
Os exemplos do Windows Communication Foundation (WCF) podem ser executados em uma configuração única máquina ou várias máquinas. Como fornecidos, os exemplos estão prontos para execução em um único computador. Em uma configuração de várias máquinas, é necessário modificar o arquivo de configuração de um exemplo. Os procedimentos a seguir explicam como executar um exemplo em configurações na mesma máquina e entre computadores. Observe que há variações nas etapas para serviços hospedados no Internet Information Services (IIS) e os exemplos de auto-hospedados. A maioria dos exemplos são hospedados no IIS; Consulte as informações do Leiame do exemplo para determinar como ele está hospedado.  
  
 Em [!INCLUDE[wv](../../../../includes/wv-md.md)], os exemplos não são hospedados em IIS exigem privilégios elevados para registrar um ouvinte HTTP. sys. Use Httpcfg.exe para registrar os endereços de escuta do serviço com a conta que de serviço está sendo executado, ou inicie o serviço em um prompt de comando com privilégios de administrador.  
  
> [!NOTE]
>  Antes de criar ou executar qualquer um dos exemplos do WCF, certifique-se que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar o exemplo na mesma máquina  
  
1.  Se o serviço é hospedado pelo IIS, certifique-se de que você pode acessar o serviço usando um navegador, digitando o seguinte endereço: http://localhost/servicemodelsamples/service.svc. Uma página de confirmação deve ser exibida na resposta. Se a página de confirmação não for exibida, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
2.  Se o serviço é auto-hospedado, execute Service.exe em \service\bin, sob a pasta de idioma específico. Atividade do serviço é exibida na janela do console de serviço.  
  
3.  Executar Client.exe de \Client\Bin.\\, sob a pasta de idioma específico. Atividade do cliente é exibida na janela do console do cliente.  
  
4.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-machines"></a>Para executar o exemplo entre máquinas  
  
1.  Se o serviço está hospedado no IIS:  
  
    1.  No computador do serviço, crie um diretório virtual chamado ServiceModelSamples. O arquivo de lote Setupvroot.bat incluído [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) pode ser usado para criar o diretório de disco e o diretório virtual.  
  
    2.  Copie os arquivos de programa do serviço de %SystemDrive%\Inetpub\wwwroot\servicemodelsamples ao diretório virtual ServiceModelSamples na máquina do serviço. Certifique-se de que você inclua os arquivos no diretório \bin.  
  
    3.  Teste que você pode acessar o serviço no computador cliente usando um navegador.  
  
     Se o serviço é auto-hospedado:  
  
    1.  No computador do serviço, crie um diretório para armazenar os arquivos de serviço.  
  
    2.  Copie os arquivos de programa de serviço da pasta \service\bin\, sob a pasta de idioma específico, para o computador de serviço.  
  
    3.  No arquivo de configuração de serviço, altere o valor do endereço da definição do ponto de extremidade para coincidir com o novo endereço do seu serviço. Substitua todas as referências a "localhost" com um nome de domínio totalmente qualificado no endereço.  
  
    4.  Inicie o Service.exe em um prompt de comando.  
  
2.  Copie os arquivos de programa do cliente da pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.  
  
3.  Defina o endereço do ponto de extremidade.  
  
    1.  Se o serviço não está em execução em uma conta de domínio, abra o arquivo de configuração do cliente e altere o valor de endereço da definição do ponto de extremidade para coincidir com o novo endereço do seu serviço. Substitua todas as referências a "localhost" com um nome de domínio totalmente qualificado no endereço.  
  
    2.  Se o serviço está em execução em uma conta de domínio, gere novamente a configuração do cliente executando Svcutil.exe no serviço. Para obter mais informações sobre como executar Svcutil.exe, consulte [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Use o arquivo gerado em vez do arquivo de configuração no exemplo. O arquivo de configuração gerada tem informações de identidade adicional e contém todas as configurações necessárias para se conectar ao ponto de extremidade de serviço, mesmo que eles sejam as configurações padrão. Para obter mais informações sobre informações de identidade, consulte [identidade de serviço e autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), e [ \<identidade >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).  
  
4.  No computador cliente, inicie Client.exe em um prompt de comando.  
  
### <a name="to-debug-a-service"></a>Para depurar um serviço  
  
1.  Compilar a solução (cliente e serviço) usando o **Build** menu ou CTRL + SHIFT + B.  
  
2.  Se o serviço está hospedado no IIS:  
  
    1.  Ativar o serviço usando um navegador, inserindo o endereço http://localhost/servicemodelsamples/service.svc.  
  
    2.  Na solução, escolha o **Debug** menu e o **anexar ao processo** item de menu.  
  
    3.  Marque a caixa de seleção **Mostrar processos de todos os usuários**.  
  
    4.  Selecione o processo de trabalho do host W3wp.exe depurar (selecione ASPNet_wp.exe no Windows XP).  
  
3.  Agora você pode definir pontos de interrupção no código de serviço e habilitar pontos de interrupção em exceções.  
  
4.  O item de projeto do cliente com o botão direito e escolha **Debug**, **iniciar nova instância**.  
  
### <a name="to-clean-up-after-the-sample"></a>Para limpar após a amostra  
  
-   Se o serviço está hospedado no IIS para fins de segurança, remova a definição do diretório virtual e as permissões concedidas nas etapas de configuração quando tiver terminado com os exemplos.  
  
## <a name="see-also"></a>Consulte também  
 [Compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
 [Executando os exemplos em um grupo de trabalho e entre máquinas](https://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113)  
 [Dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)
