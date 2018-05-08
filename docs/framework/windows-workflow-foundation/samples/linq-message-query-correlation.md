---
title: Correlação de consulta de mensagem LINQ
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 5b215764f7e02f07873f63872f4ac8c3fcaffbcc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="linq-message-query-correlation"></a>Correlação de consulta de mensagem LINQ
Este exemplo demonstra como fazer correlação conteudo base que usa uma implementação personalizada de <xref:System.ServiceModel.Dispatcher.MessageQuery> diferentemente de sistema forneceu <xref:System.ServiceModel.XPathMessageQuery>.  
  
## <a name="demonstrates"></a>Demonstra  
 <xref:System.ServiceModel.Dispatcher.MessageQuery>personalizado, correlação conteudo base.  
  
## <a name="discussion"></a>Discussão  
 Este exemplo mostra como estender a classe base de <xref:System.ServiceModel.Dispatcher.MessageQuery> para fins de correlação. A implementação personalizada, `LinqMessageQuery`, permite que os usuários forneçam um XName para localizar dentro de mensagem usando XLinq. Os dados recuperados pela consulta são usados para formar a chave de correlação para distribuir mensagens à instância apropriado de fluxo de trabalho.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Este exemplo exibe um serviço de fluxo de trabalho usando pontos de extremidade HTTP. Para executar este exemplo, adequado ACLs de URL deve ser adicionado (consulte [Configurando HTTP e HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes), executando o Visual Studio como administrador ou executando o seguinte comando em um prompt elevado para adicionar as ACLs corretas. Certifique-se de que seu domínio e nome de usuário são substituídos.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  Uma vez que o URL ACLs é adicionado, use as seguintes etapas.  
  
    1.  Compile a solução.  
  
    2.  Definir vários projetos de inicialização, clicando duas vezes a solução e selecionando **definir projetos de inicialização**. Adicionar **Service** e **cliente** (nessa ordem) como vários projetos de inicialização.  
  
    3.  Execute o aplicativo. O console de cliente mostra um fluxo de trabalho que envia um pedido e que recebe a identificação de ordem de compra e então confirma posteriormente ordem. A janela de serviço (as solicitações que estão sendo processadas.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
