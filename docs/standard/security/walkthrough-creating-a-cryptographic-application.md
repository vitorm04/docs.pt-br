---
title: "Instruções passo a passo: criando um aplicativo criptográfico"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ab596fd10de81e60e6396268cbd5c5b31aa13078
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-creating-a-cryptographic-application"></a>Instruções passo a passo: criando um aplicativo criptográfico
Este passo a passo demonstra como criptografar e descriptografar o conteúdo. Os exemplos de código são projetados para um aplicativo Windows Forms. Este aplicativo não demonstram cenários do mundo real, como o uso de cartões inteligentes. Em vez disso, ele demonstra os fundamentos da criptografia e descriptografia.  
  
 Este passo a passo usa as seguintes diretrizes para criptografia:  
  
-   Use o <xref:System.Security.Cryptography.RijndaelManaged> classe, um algoritmo simétrico, para criptografar e descriptografar dados usando gerado automaticamente <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> e <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.  
  
-   Use o <xref:System.Security.Cryptography.RSACryptoServiceProvider>, um algoritmo assimétrico, para criptografar e descriptografar a chave para os dados criptografados pela <xref:System.Security.Cryptography.RijndaelManaged>. Algoritmos assimétricos são mais adequados para pequenas quantidades de dados, como uma chave.  
  
    > [!NOTE]
    >  Se você quiser proteger os dados em seu computador, em vez de trocar o conteúdo criptografado com outras pessoas, considere o uso de <xref:System.Security.Cryptography.ProtectedData> ou <xref:System.Security.Cryptography.ProtectedMemory> classes.  
  
 A tabela a seguir resume as tarefas criptográficas neste tópico.  
  
|Tarefa|Descrição|  
|----------|-----------------|  
|Criando um aplicativo Windows Forms|Lista os controles que são necessárias para executar o aplicativo.|  
|Declarando objetos globais|Declara as variáveis de caminho, a cadeia de caracteres de <xref:System.Security.Cryptography.CspParameters>e o <xref:System.Security.Cryptography.RSACryptoServiceProvider> ter contexto global de <xref:System.Windows.Forms.Form> classe.|  
|Criando uma chave assimétrica|Cria um par de valor de chave pública e privada assimétrica e atribui a ele um nome de contêiner de chave.|  
|Criptografia de um arquivo|Exibe uma caixa de diálogo para selecionar um arquivo para criptografia e criptografa o arquivo.|  
|Descriptografar um arquivo|Exibe uma caixa de diálogo para selecionar um arquivo criptografado para descriptografar e descriptografa o arquivo.|  
|Obtendo uma chave privada|Obtém o par de chave completo usando o nome do contêiner de chave.|  
|Exportar uma chave pública|Salva a chave para um arquivo XML com apenas os parâmetros públicos.|  
|Importando uma chave pública|Carrega a chave de um arquivo XML para o contêiner de chave.|  
|Testando o aplicativo|Lista os procedimentos para testar esse aplicativo.|  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Referências aos namespaces <xref:System.IO> e <xref:System.Security.Cryptography>.  
  
## <a name="creating-a-windows-forms-application"></a>Criando um aplicativo do Windows Forms  
 A maioria dos exemplos de código neste passo a passo é projetada para serem manipuladores de eventos para controles de botão. A tabela a seguir lista os controles necessários para o aplicativo de exemplo e seus nomes necessárias corresponder os exemplos de código.  
  
|Controle|Nome|Propriedade de texto (conforme necessário)|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|Criptografar arquivo|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|Descriptografar arquivos|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|Criar chaves|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|Exportar a chave pública|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|Importar a chave pública|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|Obter a chave privada|  
|<xref:System.Windows.Forms.Label>|`label1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 Clique duas vezes os botões no designer do Visual Studio para criar seus manipuladores de eventos.  
  
## <a name="declaring-global-objects"></a>Declarando objetos globais  
 Adicione o seguinte código para o construtor do formulário. Edite as variáveis de cadeia de caracteres para o seu ambiente e preferências.  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a>Criando uma chave assimétrica  
 Esta tarefa cria uma chave assimétrica que criptografa e descriptografa o <xref:System.Security.Cryptography.RijndaelManaged> chave. Essa chave foi usada para criptografar o conteúdo e exibe o nome do contêiner de chave do controle de rótulo.  
  
 Adicione o seguinte código como o `Click` manipulador de eventos para o `Create Keys` botão (`buttonCreateAsmKeys_Click`).  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a>Criptografia de um arquivo  
 Essa tarefa envolve dois métodos: o método do manipulador de eventos para o `Encrypt File` botão (`buttonEncryptFile_Click`) e o `EncryptFile` método. O primeiro método exibe uma caixa de diálogo para selecionar um arquivo e passa o nome de arquivo para o segundo método, que realiza a criptografia.  
  
 O conteúdo criptografado, chave e IV são todas salvas em um <xref:System.IO.FileStream>, que é conhecido como o pacote de criptografia.  
  
 O `EncryptFile` método faz o seguinte:  
  
1.  Cria um <xref:System.Security.Cryptography.RijndaelManaged> algoritmo simétrico para criptografar o conteúdo.  
  
2.  Cria um <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto para criptografar o <xref:System.Security.Cryptography.RijndaelManaged> chave.  
  
3.  Usa um <xref:System.Security.Cryptography.CryptoStream> object para ler e criptografar o <xref:System.IO.FileStream> do arquivo de origem, em blocos de bytes em um destino <xref:System.IO.FileStream> objeto para o arquivo criptografado.  
  
4.  Determina os comprimentos de chave criptografada e do IV e cria as matrizes de bytes de seus valores de comprimento.  
  
5.  Grava a chave, o IV e seus valores de comprimento de pacote criptografado.  
  
 O pacote de criptografia usa o seguinte formato:  
  
-   Comprimento da chave, bytes 0 - 3  
  
-   Comprimento de IV, bytes de 4 a 7  
  
-   Chave criptografada  
  
-   IV  
  
-   Texto codificado  
  
 Você pode usar os comprimentos de chave e do IV para determinar os pontos de partida e comprimentos de todas as partes do pacote de criptografia, que pode ser usada para descriptografar o arquivo.  
  
 Adicione o seguinte código como o `Click` manipulador de eventos para o `Encrypt File` botão (`buttonEncryptFile_Click`).  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 Adicione o seguinte `EncryptFile` método para o formulário.  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a>Descriptografar um arquivo  
 Essa tarefa envolve dois métodos, o método do manipulador de eventos para o `Decrypt File` botão (`buttonEncryptFile_Click`) e o `DecryptFile` método. O primeiro método exibe uma caixa de diálogo para selecionar um arquivo e passa o nome de arquivo para o segundo método, que executa a descriptografia.  
  
 O `Decrypt` método faz o seguinte:  
  
1.  Cria um <xref:System.Security.Cryptography.RijndaelManaged> algoritmo simétrico para descriptografar o conteúdo.  
  
2.  Lê os primeiros oito bytes do <xref:System.IO.FileStream> do pacote criptografado em matrizes de bytes para obter os comprimentos de chave criptografada e o IV.  
  
3.  Extrai a chave e a IV do pacote de criptografia para matrizes de bytes.  
  
4.  Cria um <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto para descriptografar o <xref:System.Security.Cryptography.RijndaelManaged> chave.  
  
5.  Usa um <xref:System.Security.Cryptography.CryptoStream> object para ler e descriptografar a seção de texto cifrado do <xref:System.IO.FileStream> criptografia do pacote, em blocos de bytes, para o <xref:System.IO.FileStream> objeto para o arquivo descriptografado. Quando isso for concluído, a descriptografia é concluída.  
  
 Adicione o seguinte código como o `Click` manipulador de eventos para o `Decrypt File` botão.  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 Adicione o seguinte `DecryptFile` método para o formulário.  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a>Exportar uma chave pública  
 Essa tarefa salva a chave criada pelo `Create Keys` botão em um arquivo. Ele exporta somente os parâmetros públicos.  
  
 Essa tarefa simula o cenário de Alice fornecendo Bob sua chave pública para que ele pode criptografar os arquivos para ela. Ele e outros que têm essa chave pública não poderá descriptografá-los porque eles não têm o par de chave completo com parâmetros privados.  
  
 Adicione o seguinte código como o `Click` manipulador de eventos para o `Export Public Key` botão (`buttonExportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a>Importando uma chave pública  
 Essa tarefa carrega a chave pública apenas parâmetros, conforme criado pelo `Export Public Key` botão e, em seguida, define como o nome do contêiner de chave.  
  
 Essa tarefa simula o cenário de Bob carregando a chave de Alice com apenas os parâmetros públicos para que ele pode criptografar os arquivos para ela.  
  
 Adicione o seguinte código como o `Click` manipulador de eventos para o `Import Public Key` botão (`buttonImportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a>Obtendo uma chave privada  
 Essa tarefa define o nome do contêiner de chave com o nome da chave criada usando o `Create Keys` botão. O contêiner de chave contém o par de chave completo com parâmetros privados.  
  
 Essa tarefa simula o cenário de Alice usando sua chave privada para descriptografar arquivos criptografados pelo Bob.  
  
 Adicione o seguinte código como o `Click` manipulador de eventos para o `Get Private Key` botão (`buttonGetPrivateKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Depois de criar o aplicativo, execute os seguintes cenários de teste.  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a>Para criar chaves, criptografar e descriptografar  
  
1.  Clique no botão `Create Keys`. O rótulo exibe o nome da chave e mostra o que é um par de chave completo.  
  
2.  Clique no botão `Export Public Key`. Observe que a exportação de parâmetros de chave públicos não altera a chave atual.  
  
3.  Clique o `Encrypt File` botão e selecione um arquivo.  
  
4.  Clique o `Decrypt File` botão e selecione o arquivo criptografado apenas.  
  
5.  Examine o arquivo apenas descriptografado.  
  
6.  Feche o aplicativo e reiniciá-lo para testar a recuperar contêineres de chave persistentes no seguinte cenário.  
  
#### <a name="to-encrypt-using-the-public-key"></a>Para criptografar usando a chave pública  
  
1.  Clique no botão `Import Public Key`. O rótulo exibe o nome da chave e mostra o que é público apenas.  
  
2.  Clique o `Encrypt File` botão e selecione um arquivo.  
  
3.  Clique o `Decrypt File` botão e selecione o arquivo criptografado apenas. Isso irá falhar porque você deve ter a chave privada para descriptografar.  
  
 Este cenário demonstra ter apenas a chave pública para criptografar um arquivo para outra pessoa. Normalmente essa pessoa lhe somente a chave pública e a chave privada para descriptografia de retenção.  
  
#### <a name="to-decrypt-using-the-private-key"></a>Para descriptografar usando a chave privada  
  
1.  Clique no botão `Get Private Key`. O rótulo exibe o nome da chave e mostra se ele é o par de chave completo.  
  
2.  Clique o `Decrypt File` botão e selecione o arquivo criptografado apenas. Isso será bem-sucedida porque você tem o par de chave completo para descriptografar.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)
