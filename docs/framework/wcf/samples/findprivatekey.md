---
title: Exemplo de FindPrivateKey – WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 72e2f49ae7c39b4a0486ec053ff1164c2d833cbe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990087"
---
# <a name="findprivatekey-sample"></a>Exemplo de FindPrivateKey

Ele pode ser difícil encontrar o local e o nome do arquivo de chave privada associado com um certificado x. 509 específico no repositório de certificados. A ferramenta FindPrivateKey.exe facilita esse processo.

> [!IMPORTANT]
> FindPrivateKey é um exemplo que precisa ser compilado antes do uso. Consulte a [para compilar o projeto FindPrivateKey](#to-build-the-findprivatekey-project) seção para obter instruções sobre como compilar a ferramenta FindPrivateKey.

Certificados x. 509 são instalados por um administrador ou a qualquer usuário na máquina. No entanto, o certificado pode ser acessado por um serviço executado sob uma conta diferente. Por exemplo, a conta de serviço de rede.

Essa conta pode não ter acesso ao arquivo de chave privada porque o certificado não foram instalado originalmente por ele. A ferramenta FindPrivateKey fornece o local do arquivo de chave privada do certificado X.509 especificado. Você pode adicionar permissões ou remover permissões para esse arquivo, se você souber o local do arquivo de chave privada dos certificados x. 509 específico.

Os exemplos que usam certificados para segurança de usam a ferramenta de FindPrivateKey na *Setup. bat* arquivo. Depois que o arquivo de chave privada foi encontrado, você pode usar outras ferramentas, como *Cacls.exe* para definir os direitos de acesso apropriados para o arquivo.

Ao executar um serviço do Windows Communication Foundation (WCF) em uma conta de usuário, como um executável auto-hospedado, certifique-se de que a conta de usuário tem acesso somente leitura para o arquivo. Ao executar um serviço WCF em serviços de informações da Internet (IIS) as contas padrão que o serviço é executado são o serviço de rede no IIS 7 e versões anteriores, ou a identidade do Pool de aplicativos no IIS 7.5 e versões posteriores. Para obter mais informações, consulte [identidades do Pool de aplicativos](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Exemplos

Ao acessar um certificado para o qual o processo não tem o privilégio de leitura, você verá uma mensagem de exceção semelhante ao exemplo a seguir:

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

Quando isso ocorrer, use a ferramenta de FindPrivateKey para localizar o arquivo de chave privada e, em seguida, defina o direito de acesso para o processo que o serviço está sendo executado. Por exemplo, isso pode ser feito com a ferramenta Cacls.exe, conforme mostrado no exemplo a seguir:

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>Para compilar o projeto FindPrivateKey

Para baixar o projeto, visite [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

1. Abra [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] e navegue até a *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* pasta sob o local do diretório onde você instalou o exemplo.

2. Clique duas vezes no ícone do arquivo. sln para abrir o arquivo no Visual Studio.

3. No **construir** menu, selecione **recompilar solução**.

4. Compilando a solução gera o arquivo: FindPrivateKey.exe.

## <a name="conventionscommand-line-entries"></a>Convenções — entradas de linha de comando

 "[*opção*]" representa um conjunto opcional de parâmetros.

 "{*opção*}" representa um conjunto obrigatório de parâmetros.

 "*option1* &#124; *option2*" representa uma opção entre conjuntos de opções.

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

Este exemplo localiza o nome do arquivo do certificado com um nome de entidade "CN = localhost", no repositório pessoal do usuário atual.

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

Este exemplo localiza o nome do arquivo do certificado com um nome de entidade "CN = localhost", no perfil pessoal armazenar do usuário atual e o caminho completo do diretório de saída.

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

Este exemplo localiza o nome do arquivo do certificado com impressão digital "03 33 98 63 e7 de 47 d0 48 71 33 62 64 76 5c 4c 9D 1 de 42 6b d 52", no repositório pessoal do computador Local.

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
