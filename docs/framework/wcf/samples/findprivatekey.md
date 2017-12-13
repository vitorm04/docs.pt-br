---
title: Exemplo de FindPrivateKey - WCF
ms.date: 12/04/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 29489cd1b82cf1c31f178d8a305a21371b542f15
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2017
---
# <a name="findprivatekey-sample"></a>Exemplo de FindPrivateKey

Pode ser difícil encontrar o local e o nome do arquivo da chave privado associado com um certificado x. 509 específico no repositório de certificados. A ferramenta FindPrivateKey.exe facilita esse processo.

> [!IMPORTANT]
> FindPrivateKey é um exemplo que devem ser compilados antes do uso. Consulte o [para compilar o projeto FindPrivateKey](#to-build-the-findprivatekey-project) seção para obter instruções sobre como criar a ferramenta FindPrivateKey.

Certificados x. 509 são instalados por um administrador ou a qualquer usuário na máquina. No entanto, o certificado pode ser acessado por um serviço executado sob uma conta diferente. Por exemplo, a conta de serviço de rede.

Essa conta pode não ter acesso ao arquivo de chave privado porque o certificado não foram instalado originalmente por ele. A ferramenta FindPrivateKey fornece o local do arquivo de chave privada do certificado x. 509 determinado. Você pode adicionar permissões ou remover permissões para esse arquivo quando você souber o local do arquivo de chave privada dos certificados x. 509 específico.

Os exemplos que usam certificados para segurança de usam a ferramenta de FindPrivateKey no *bat* arquivo. Depois que o arquivo de chave privada for encontrado, você pode usar outras ferramentas, como *Cacls.exe* para definir os direitos de acesso apropriados para o arquivo.

Quando a execução de um serviço do Windows Communication Foundation (WCF) em uma conta de usuário, como um executável auto-hospedado, certifique-se de que a conta de usuário tem acesso somente leitura ao arquivo. Ao executar um serviço WCF em serviços de informações da Internet (IIS) as contas padrão que o serviço é executado são o serviço de rede no IIS 7 e versões anteriores, ou a identidade do Pool de aplicativos no IIS 7.5 e versões posteriores. Para obter mais informações, consulte [identidades do Pool de aplicativos](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Exemplos

Ao acessar um certificado para o qual o processo não tem o privilégio de leitura, verá uma mensagem de exceção semelhante ao exemplo a seguir:

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

Quando isso ocorrer, use a ferramenta de FindPrivateKey para localizar o arquivo de chave privada e, em seguida, defina o acesso à direita para o processo que o serviço está em execução em. Por exemplo, isso pode ser feito com a ferramenta Cacls.exe, conforme mostrado no exemplo a seguir:

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>Para compilar o projeto FindPrivateKey

Para baixar o projeto, visite [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

1. Abra [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] e navegue até o *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* pasta sob o local do diretório onde você instalou o exemplo.

2. Clique duas vezes no ícone do arquivo. sln para abrir o arquivo no Visual Studio.

3. No **criar** menu, selecione **recompilar solução**.

4. Compilar a solução gera o arquivo: FindPrivateKey.exe.

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

Se nenhum parâmetro for especificado no prompt de comando, este texto de Ajuda é exibido.

## <a name="examples"></a>Exemplos

Este exemplo localiza o nome do arquivo do certificado com um nome de assunto de "CN = localhost", no repositório pessoal do usuário atual.

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

Este exemplo localiza o nome do arquivo do certificado com um nome de assunto de "CN = localhost", em que o pessoal armazenar do usuário atual e o caminho completo do diretório de saída.

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

Este exemplo localiza o nome do arquivo do certificado com impressão digital "03 33 98 63 e7 47 d0 48 71 33 62 64 76 5c 4c 9d 1 de 42 6b d 52", no repositório pessoal do computador Local.

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
