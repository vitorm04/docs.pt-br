---
title: FindPrivateKey
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81ca357ccdcbe76f36f3ba56caf2013a80143728
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="findprivatekey"></a>FindPrivateKey
Pode ser difícil encontrar o local e o nome do arquivo da chave privado associado com um certificado x. 509 específico no repositório de certificados. A ferramenta FindPrivateKey.exe facilita esse processo.  
  
> [!IMPORTANT]
>  FindPrivateKey é um exemplo que devem ser compilados antes do uso. Consulte a seção "para criar o projeto de FindPrivateKey" abaixo para obter instruções sobre como criar a ferramenta FindPrivateKey.  
  
 Certificados x. 509 são instalados por um administrador ou a qualquer usuário na máquina. No entanto, o certificado pode ser acessado por um serviço executado sob uma conta diferente (por exemplo, o ASPNET em [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou as contas de serviço de rede em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).  
  
 Essa conta pode não ter acesso ao arquivo de chave privado porque o certificado não foram instalado originalmente por ele. A ferramenta FindPrivateKey fornece o local do arquivo de chave privada do certificado x. 509 determinado. Você pode adicionar permissões ou remover permissões para esse arquivo quando você souber o local do arquivo de chave privada dos certificados x. 509 específico.  
  
 Os exemplos que usam certificados para segurança de usam a ferramenta de FindPrivateKey no arquivo bat. Depois que o arquivo de chave privada foi encontrado, você pode usar outras ferramentas, como Cacls.exe para definir os direitos de acesso apropriados para o arquivo.  
  
 Ao executar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço sob uma conta de usuário, como um executável auto-hospedado, certifique-se de que a conta de usuário tem acesso somente leitura ao arquivo. Ao executar uma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço em Internet Information Services (IIS) as contas padrão que o serviço é executado são o ASPNET em [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou o serviço de rede em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], que por padrão não tem acesso ao arquivo de chave privado.  
  
## <a name="examples"></a>Exemplos  
 Ao acessar um certificado para o qual o processo não tem o privilégio de leitura, verá uma mensagem de exceção semelhante ao exemplo a seguir.  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 Quando isso ocorre use a ferramenta de FindPrivateKey para localizar o arquivo de chave privada e, em seguida, defina o acesso certo para o processo que o serviço está em execução. Por exemplo, isso pode ser feito com a ferramenta Cacls.exe, conforme mostrado no exemplo a seguir.  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a>Para compilar o projeto FindPrivateKey  
  
1.  Abra [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] e navegue até o subdiretório específico do idioma em que o local do diretório onde você instalou o exemplo.  
  
2.  Clique duas vezes no ícone do arquivo. sln para abrir o arquivo no Visual Studio.  
  
3.  No **criar** menu, selecione **recompilar solução**. Os arquivos de programa do cliente são criados para client\bin e os arquivos de programa de serviço são criados para service\bin.  
  
4.  Compilar a solução gera o arquivo: FindPrivateKey.exe.  
  
## <a name="conventionscommand-line-entries"></a>Convenções — entradas de linha de comando  
 "[*opção*]" representa um conjunto opcional de parâmetros.  
  
 "{*opção*}" representa um conjunto de parâmetros de obrigatório.  
  
 "*opção 1* &#124; *option2*"representa uma opção entre conjuntos de opções.  
  
 "\<*valor*>" representa um valor de parâmetro a ser inserido.  
  
## <a name="usage"></a>Uso  
  
```  
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
 Sendo que:  
  
```  
       <subjectName> The subject name of the certificate  
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)  
       -f            output file name only  
       -d            output directory only  
       -a            output absolute file name  
```  
  
 Se nenhum parâmetro for especificado no prompt de comando, este texto de Ajuda será exibido.  
  
## <a name="examples"></a>Exemplos  
 Este exemplo localiza o nome do arquivo do certificado com um nome de assunto de "CN = localhost", no repositório pessoal do atual User.FindPrivateKey e meu CurrentUser - n "CN = localhost".  
  
 Este exemplo localiza o nome do arquivo do certificado com um nome de assunto de "CN = localhost", em que o pessoal armazenar de atual e o caminho completo do diretório de saída.  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 Este exemplo localiza o nome do arquivo do certificado com impressão digital "03 33 98 63 e7 47 d0 48 71 33 62 64 76 5c 4c 9d 1 de 42 6b d 52", no repositório pessoal do computador Local.  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a>Consulte também
