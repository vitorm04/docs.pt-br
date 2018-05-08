---
title: Interpretando os códigos de erro retornados pelo wsatConfig.exe
ms.date: 03/30/2017
ms.assetid: ab65f22b-0d69-4c21-9aaf-74acef0ca102
ms.openlocfilehash: 9df059618b45ae65ffb3e6e31a87d5531c79d947
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="interpreting-error-codes-returned-by-wsatconfigexe"></a>Interpretando os códigos de erro retornados pelo wsatConfig.exe
Este tópico lista todos os códigos de erro gerado pelo utilitário de configuração do WS-AtomicTransaction (wsatConfig.exe) e as ações recomendadas para ser executada.  
  
## <a name="list-of-error-codes"></a>Lista de códigos de erro  
  
|Código do erro|Descrição|Ação recomendada para ser executada|  
|----------------|-----------------|------------------------------------|  
|0|A operação foi bem-sucedida|Nenhum|  
|1|Erro inesperado|Entre em contato com a Microsoft|  
|2|Um erro inesperado ocorreu ao tentar contatar o MSDTC para recuperar as configurações de segurança.|Certifique-se de que o serviço MSDTC não está desabilitado e resolver todos os problemas listados na exceção retornada.|  
|3|A conta sob a qual WsatConfig.exe foi executado não tem permissões suficientes para ler as configurações de segurança de rede.|Execute WsatConfig.exe sob uma conta de administrador.|  
|4|Habilite "Acesso DTC de rede" para o MSDTC antes de tentar habilitar o suporte do WS-AT.|Habilitar "Acesso DTC de rede" para o MSDTC e execute novamente o utilitário.|  
|5|A porta inserida estava fora do intervalo. O valor deve estar no intervalo de 1 a 65535.|Corrija o `-port:<portNum>`<br /><br /> opção de linha de comando, conforme indicado na mensagem de erro.|  
|6|Um certificado de ponto de extremidade inválido foi especificado na linha de comando.  Não foi possível encontrar o certificado ou ele não passou na verificação.|Corrija o `-endpointCert` opção de linha de comando. Certifique-se de que o certificado tem uma chave privada, se destina a ser usado para autenticação de servidor e ClientAuthentication, está instalado no repositório de certificados LocalMachine\MY e é totalmente confiável.|  
|7|Um certificado de contas inválido foi especificado na linha de comando.|Corrija o `-accountsCerts` opção de linha de comando. O certificado especificado incorretamente foi especificado ou não foi encontrado.|  
|8|Tempo limite padrão foi especificado fora do intervalo de 1 a 3.600 segundos.|Insira um valor de tempo limite padrão correto, conforme indicado.|  
|10|Ocorreu um erro inesperado ao tentar acessar o registro.|Verifique a mensagem de erro e o código de erro para itens acionáveis|  
|11|Não é possível gravar no registro.|Certifique-se de que a chave listada na mensagem de erro é capaz de dar suporte a acesso de registro da conta de em que wsatconfig.exe foi executada.|  
|12|Ocorreu um erro inesperado ao tentar acessar o repositório de certificados.|Use o código de erro retornado para mapear para o erro de sistema apropriado.|  
|13|Falha na configuração do HTTP. sys. Não é possível criar uma nova reserva de porta HTTPS para o MSDTC.|Use o código de erro retornado para mapear para o erro de sistema apropriado.|  
|14|Falha na configuração do HTTP. sys. Não é possível remover a reserva de porta HTTPS anterior para o MSDTC.|Use o código de erro retornado para mapear para o erro de sistema apropriado.|  
|15|Falha na configuração do HTTP. sys. Uma reserva porta HTTPS anterior já existe para a porta especificada.|Outro aplicativo já tem assumir a propriedade da porta específica. Alterar para uma porta diferente ou desinstalar ou reconfigurar o aplicativo atual.|  
|16|Falha na configuração do HTTP. sys. Não é possível associar o certificado especificado para a porta.|Use o código de erro retornado na mensagem de erro para mapear para o erro de sistema apropriado|  
|17|Falha na configuração do HTTP. sys. Não é possível desvincular o certificado SSL da porta anterior.|Use o código de erro retornado na mensagem de erro para mapear para o erro de sistema apropriado. Se necessário, use httpcfg.exe ou netsh.exe para remover as reservas de porta errado.|  
|18|Falha na configuração do HTTP. sys. Não é possível associar o certificado especificado para a porta porque um SSL anterior associação já existe.|Outro aplicativo já tem assumir a propriedade da porta específica. Alterar para uma porta diferente ou desinstalar ou reconfigurar o aplicativo atual.|  
|19|Falha ao reiniciar o MSDTC|Reinicie manualmente o MSDTC se necessário. Se o problema persistir, contate a Microsoft.|  
|20|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] não está instalado no computador remoto, ou não está instalado corretamente.|Instalar [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] na máquina.|  
|21|Configuração remota falhou devido a tempo a operação limite.|A chamada para configurar WS-AT na máquina remota deve levar mais de 90 segundos.|  
|22|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] não está instalado no computador remoto, ou não está instalado corretamente.|Instalar [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] na máquina.|  
|23|Configuração remota falhou devido a uma exceção no computador remoto.|Verifique a mensagem de erro para itens acionáveis|  
|26|Um argumento inválido foi passado para WsatConfig.exe.|Verifique a linha de comando para erros.|  
|27|O `-accounts` opção de linha de comando era inválida.|Corrija-`accounts` opção de linha de comando para especificar corretamente uma conta de usuário.|  
|28|O `-network` opção de linha de comando era inválida.|Corrija o `-network` opção de linha de comando para especificar corretamente "Habilitar" ou "Desabilitar".|  
|29|O `-maxTimeout` opção de linha de comando era inválida.|Corrija o `-maxTimeout` opção de linha de comando, conforme indicado.|  
|30|O `-timeout` opção de linha de comando era inválida.|Corrija o `-timeout` opção de linha de comando, conforme indicado.|  
|31|O `-traceLevel` opção de linha de comando era inválida.|Corrija o `-traceLevel` opção de linha de comando para especificar um valor válido da seguinte,<br /><br /> -Off<br />-Erro<br />–   Crítica<br />-Aviso<br />-Informações<br />-Verbose<br />-Todos os itens|  
|32|O `-traceActivity` opção de linha de comando era inválida.|Corrija o `-traceActivity` opção de linha de comando, especificando "Habilitar" ou "Desabilitar".|  
|33|O `-traceProp` opção de linha de comando era inválida.|Corrija o `-traceProp` opção de linha de comando, especificando "Habilitar" ou "Desabilitar".|  
|34|O `-tracePII` opção de linha de comando era inválida.|Corrija o `-tracePII` opção de linha de comando, especificando "Habilitar" ou "Desabilitar".|  
|37|WsatConfig.exe não pôde determinar o certificado do computador exata. Isso pode acontecer quando há mais de um candidato, ou quando não houver nenhuma.|Especifique uma impressão digital do certificado ou pelo par Issuer\SubjectName. para identificar corretamente o certificado exato para configurar.|  
|38|O processo ou o usuário não tem permissões suficientes para alterar a configuração de firewall.|Execute WsatConfig.exe sob uma conta de administrador.|  
|39|WsatConfig.exe encontrou um erro ao atualizar a configuração do firewall.|Verifique a mensagem de erro para itens acionáveis.|  
|40|WsatConfig.exe não é capaz de conceder acesso de leitura de MSDTC para o arquivo de chave privada do certificado|Execute WsatConfig.exe sob uma conta de administrador.|  
|41|Ou nenhuma instalação do [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] pode ser encontrado ou a versão encontrada não coincide com o que é capaz de configurar a ferramenta.|Certifique-se de [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] é corretamente instalado e apenas use a ferramenta de WsatConfig.exe que acompanha a versão do [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] para configurar WS-AT.|  
|42|Um argumento foi especificado mais de uma vez na linha de comando.|Só especifique cada argumento de uma vez ao executar WsatConfig.exe.|  
|43|WsatConfig.exe não é possível atualizar as configurações do WS-AT se WS-AT não está habilitado.|Especifique `-network:enable` como um argumento de linha de comando adicionais.|  
|44|Está faltando um hotfix necessário e WS-AT não pode ser configurado até que a instalação do hotfix.|Consulte o [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] notas de versão para obter instruções sobre como instalar o hotfix necessário.|  
|45|O `-virtualServer` opção de linha de comando era inválida.|Corrija o `-virtualServer` opção de linha de comando, especificando o nome de rede do recurso de cluster na qual deseja configurar.|  
|46|Ocorreu um erro inesperado ao tentar iniciar a sessão de rastreamento ETW|Use o código de erro retornado para mapear para o erro de sistema apropriado.|  
|47|O processo ou o usuário não tem permissões suficientes para habilitar a sessão de rastreamento ETW.|Execute WsatConfig.exe sob uma conta de administrador.|  
|48|Ocorreu um erro inesperado ao tentar iniciar a sessão de rastreamento ETW.|Entre em contato com a Microsoft.|  
|49|Não é possível criar um novo arquivo de log devido a espaço insuficiente em % systemdrive %|Certifique-se de que o % systemdrive % tem espaço suficiente para o arquivo de log.|  
|51|Ocorreu um erro inesperado ao tentar iniciar a sessão de rastreamento ETW.|Entre em contato com a Microsoft.|  
|52|Ocorreu um erro inesperado ao tentar iniciar a sessão de rastreamento ETW.|Entre em contato com a Microsoft.|  
|53|Backup do arquivo de log de sessão ETW anterior não foi bem-sucedida.|Certifique-se de que o % systemdrive % tem espaço suficiente para o arquivo de log e o backup do arquivo de log anterior (se houver). Remova manualmente o arquivo de log anterior se necessário.|  
|55|Ocorreu um erro inesperado ao tentar iniciar a sessão de rastreamento ETW.|Entre em contato com a Microsoft.|  
|56|Ocorreu um erro inesperado ao tentar iniciar a sessão de rastreamento ETW.|Entre em contato com a Microsoft.|  
  
## <a name="see-also"></a>Consulte também  
 [Utilitário de configuração de WS-AtomicTransaction (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
