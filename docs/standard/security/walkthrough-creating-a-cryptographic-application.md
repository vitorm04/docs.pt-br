---
title: 'Passo a passo: criar um aplicativo criptográfico'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f141f21f80275a592caf3f87a5cbe0def6869c0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341758"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="83d17-102">Passo a passo: criar um aplicativo criptográfico</span><span class="sxs-lookup"><span data-stu-id="83d17-102">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="83d17-103">Este passo a passo demonstra como criptografar e descriptografar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="83d17-103">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="83d17-104">Os exemplos de código são projetados para um aplicativo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="83d17-104">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="83d17-105">Este aplicativo não demonstram cenários do mundo real, como o uso de cartões inteligentes.</span><span class="sxs-lookup"><span data-stu-id="83d17-105">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="83d17-106">Em vez disso, ele demonstra os conceitos básicos de criptografia e descriptografia.</span><span class="sxs-lookup"><span data-stu-id="83d17-106">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="83d17-107">Este passo a passo usa as seguintes diretrizes para criptografia:</span><span class="sxs-lookup"><span data-stu-id="83d17-107">This walkthrough uses the following guidelines for encryption:</span></span>  
  
-   <span data-ttu-id="83d17-108">Use o <xref:System.Security.Cryptography.RijndaelManaged> classe, um algoritmo simétrico, para criptografar e descriptografar dados usando gerada automaticamente <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> e <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span><span class="sxs-lookup"><span data-stu-id="83d17-108">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
-   <span data-ttu-id="83d17-109">Use o <xref:System.Security.Cryptography.RSACryptoServiceProvider>, um algoritmo assimétrico, para criptografar e descriptografar a chave para os dados criptografados pela <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="83d17-109">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="83d17-110">Algoritmos assimétricos são melhor usados para pequenas quantidades de dados, como uma chave.</span><span class="sxs-lookup"><span data-stu-id="83d17-110">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="83d17-111">Se você quiser proteger os dados em seu computador, em vez de trocar o conteúdo criptografado com outras pessoas, considere usar o <xref:System.Security.Cryptography.ProtectedData> ou <xref:System.Security.Cryptography.ProtectedMemory> classes.</span><span class="sxs-lookup"><span data-stu-id="83d17-111">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="83d17-112">A tabela a seguir resume as tarefas criptográficas neste tópico.</span><span class="sxs-lookup"><span data-stu-id="83d17-112">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="83d17-113">Tarefa</span><span class="sxs-lookup"><span data-stu-id="83d17-113">Task</span></span>|<span data-ttu-id="83d17-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="83d17-114">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="83d17-115">Criando um aplicativo Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83d17-115">Creating a Windows Forms application</span></span>|<span data-ttu-id="83d17-116">Lista os controles que são necessários para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="83d17-116">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="83d17-117">Declarando objetos globais</span><span class="sxs-lookup"><span data-stu-id="83d17-117">Declaring global objects</span></span>|<span data-ttu-id="83d17-118">Declara as variáveis de caminho, a cadeia de caracteres a <xref:System.Security.Cryptography.CspParameters>e o <xref:System.Security.Cryptography.RSACryptoServiceProvider> ter contexto global do <xref:System.Windows.Forms.Form> classe.</span><span class="sxs-lookup"><span data-stu-id="83d17-118">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="83d17-119">Criando uma chave assimétrica</span><span class="sxs-lookup"><span data-stu-id="83d17-119">Creating an asymmetric key</span></span>|<span data-ttu-id="83d17-120">Cria um par de valor de chave pública e privada assimétricas e atribui a ele um nome de contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="83d17-120">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="83d17-121">Criptografia de um arquivo</span><span class="sxs-lookup"><span data-stu-id="83d17-121">Encrypting a file</span></span>|<span data-ttu-id="83d17-122">Exibe uma caixa de diálogo para selecionar um arquivo para criptografia e criptografa o arquivo.</span><span class="sxs-lookup"><span data-stu-id="83d17-122">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="83d17-123">Descriptografar um arquivo</span><span class="sxs-lookup"><span data-stu-id="83d17-123">Decrypting a file</span></span>|<span data-ttu-id="83d17-124">Exibe uma caixa de diálogo para selecionar um arquivo criptografado para descriptografia e descriptografa o arquivo.</span><span class="sxs-lookup"><span data-stu-id="83d17-124">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="83d17-125">Obtendo uma chave privada</span><span class="sxs-lookup"><span data-stu-id="83d17-125">Getting a private key</span></span>|<span data-ttu-id="83d17-126">Obtém o par de chave completo usando o nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="83d17-126">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="83d17-127">Exportação de uma chave pública</span><span class="sxs-lookup"><span data-stu-id="83d17-127">Exporting a public key</span></span>|<span data-ttu-id="83d17-128">Salva a chave em um arquivo XML com apenas os parâmetros públicos.</span><span class="sxs-lookup"><span data-stu-id="83d17-128">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="83d17-129">Importando uma chave pública</span><span class="sxs-lookup"><span data-stu-id="83d17-129">Importing a public key</span></span>|<span data-ttu-id="83d17-130">Carrega a chave de um arquivo XML para o contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="83d17-130">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="83d17-131">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="83d17-131">Testing the application</span></span>|<span data-ttu-id="83d17-132">Lista os procedimentos para testar este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="83d17-132">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="83d17-133">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="83d17-133">Prerequisites</span></span>  
 <span data-ttu-id="83d17-134">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="83d17-134">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="83d17-135">Referências aos namespaces <xref:System.IO> e <xref:System.Security.Cryptography>.</span><span class="sxs-lookup"><span data-stu-id="83d17-135">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="83d17-136">Criando um aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83d17-136">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="83d17-137">A maioria dos exemplos de código neste passo a passo é projetada para serem manipuladores de eventos para controles de botão.</span><span class="sxs-lookup"><span data-stu-id="83d17-137">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="83d17-138">A tabela a seguir lista os controles necessários para o aplicativo de exemplo e seus nomes necessárias corresponder os exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="83d17-138">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="83d17-139">Controle</span><span class="sxs-lookup"><span data-stu-id="83d17-139">Control</span></span>|<span data-ttu-id="83d17-140">Nome</span><span class="sxs-lookup"><span data-stu-id="83d17-140">Name</span></span>|<span data-ttu-id="83d17-141">Propriedade de texto (conforme necessário)</span><span class="sxs-lookup"><span data-stu-id="83d17-141">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="83d17-142">Criptografar arquivo</span><span class="sxs-lookup"><span data-stu-id="83d17-142">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="83d17-143">Descriptografar arquivo</span><span class="sxs-lookup"><span data-stu-id="83d17-143">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="83d17-144">Criar chaves</span><span class="sxs-lookup"><span data-stu-id="83d17-144">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="83d17-145">Exportar a chave pública</span><span class="sxs-lookup"><span data-stu-id="83d17-145">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="83d17-146">Importar a chave pública</span><span class="sxs-lookup"><span data-stu-id="83d17-146">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="83d17-147">Obter a chave privada</span><span class="sxs-lookup"><span data-stu-id="83d17-147">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="83d17-148">Clique duas vezes os botões no designer do Visual Studio para criar os manipuladores de evento.</span><span class="sxs-lookup"><span data-stu-id="83d17-148">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="83d17-149">Declarando objetos globais</span><span class="sxs-lookup"><span data-stu-id="83d17-149">Declaring Global Objects</span></span>  
 <span data-ttu-id="83d17-150">Adicione o seguinte código ao construtor do formulário.</span><span class="sxs-lookup"><span data-stu-id="83d17-150">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="83d17-151">Edite as variáveis de cadeia de caracteres para seu ambiente e preferências.</span><span class="sxs-lookup"><span data-stu-id="83d17-151">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="83d17-152">Criando uma chave assimétrica</span><span class="sxs-lookup"><span data-stu-id="83d17-152">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="83d17-153">Esta tarefa cria uma chave assimétrica que criptografa e descriptografa o <xref:System.Security.Cryptography.RijndaelManaged> chave.</span><span class="sxs-lookup"><span data-stu-id="83d17-153">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="83d17-154">Essa chave foi usada para criptografar o conteúdo e exibe o nome do contêiner de chave no controle de rótulo.</span><span class="sxs-lookup"><span data-stu-id="83d17-154">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="83d17-155">Adicione o seguinte código como o `Click` manipulador de eventos para o `Create Keys` botão (`buttonCreateAsmKeys_Click`).</span><span class="sxs-lookup"><span data-stu-id="83d17-155">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="83d17-156">Criptografia de um arquivo</span><span class="sxs-lookup"><span data-stu-id="83d17-156">Encrypting a File</span></span>  
 <span data-ttu-id="83d17-157">Essa tarefa envolve dois métodos: o método de manipulador de eventos para o `Encrypt File` botão (`buttonEncryptFile_Click`) e o `EncryptFile` método.</span><span class="sxs-lookup"><span data-stu-id="83d17-157">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="83d17-158">O primeiro método exibe uma caixa de diálogo para selecionar um arquivo e passa o nome de arquivo para o segundo método, que realiza a criptografia.</span><span class="sxs-lookup"><span data-stu-id="83d17-158">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="83d17-159">O conteúdo criptografado, chave e IV são todas salvas em um <xref:System.IO.FileStream>, que é conhecido como o pacote de criptografia.</span><span class="sxs-lookup"><span data-stu-id="83d17-159">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="83d17-160">O `EncryptFile` método faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="83d17-160">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="83d17-161">Cria um <xref:System.Security.Cryptography.RijndaelManaged> algoritmo simétrico para criptografar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="83d17-161">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="83d17-162">Cria uma <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto para criptografar o <xref:System.Security.Cryptography.RijndaelManaged> chave.</span><span class="sxs-lookup"><span data-stu-id="83d17-162">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3. <span data-ttu-id="83d17-163">Usa um <xref:System.Security.Cryptography.CryptoStream> objeto leia e criptografar as <xref:System.IO.FileStream> do arquivo de origem, em blocos de bytes em um destino <xref:System.IO.FileStream> objeto para o arquivo criptografado.</span><span class="sxs-lookup"><span data-stu-id="83d17-163">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="83d17-164">Determina os comprimentos do IV e a chave criptografada e cria as matrizes de bytes de seus valores de comprimento.</span><span class="sxs-lookup"><span data-stu-id="83d17-164">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="83d17-165">Grava a chave, IV e seus valores de comprimento para o pacote criptografado.</span><span class="sxs-lookup"><span data-stu-id="83d17-165">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="83d17-166">O pacote de criptografia usa o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="83d17-166">The encryption package uses the following format:</span></span>  
  
-   <span data-ttu-id="83d17-167">Comprimento da chave, bytes de 0 - 3</span><span class="sxs-lookup"><span data-stu-id="83d17-167">Key length, bytes 0 - 3</span></span>  
  
-   <span data-ttu-id="83d17-168">Comprimento de IV, bytes de 4 a 7</span><span class="sxs-lookup"><span data-stu-id="83d17-168">IV length, bytes 4 - 7</span></span>  
  
-   <span data-ttu-id="83d17-169">Chave criptografada</span><span class="sxs-lookup"><span data-stu-id="83d17-169">Encrypted key</span></span>  
  
-   <span data-ttu-id="83d17-170">IV</span><span class="sxs-lookup"><span data-stu-id="83d17-170">IV</span></span>  
  
-   <span data-ttu-id="83d17-171">Texto codificado</span><span class="sxs-lookup"><span data-stu-id="83d17-171">Cipher text</span></span>  
  
 <span data-ttu-id="83d17-172">Você pode usar os comprimentos da chave e IV para determinar os pontos de partida e comprimentos de todas as partes do pacote de criptografia, que, em seguida, pode ser usado para descriptografar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="83d17-172">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="83d17-173">Adicione o seguinte código como o `Click` manipulador de eventos para o `Encrypt File` botão (`buttonEncryptFile_Click`).</span><span class="sxs-lookup"><span data-stu-id="83d17-173">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="83d17-174">Adicione o seguinte `EncryptFile` método ao formulário.</span><span class="sxs-lookup"><span data-stu-id="83d17-174">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="83d17-175">Descriptografar um arquivo</span><span class="sxs-lookup"><span data-stu-id="83d17-175">Decrypting a File</span></span>  
 <span data-ttu-id="83d17-176">Essa tarefa envolve dois métodos, o método de manipulador de eventos para o `Decrypt File` botão (`buttonDecryptFile_Click`) e o `DecryptFile` método.</span><span class="sxs-lookup"><span data-stu-id="83d17-176">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="83d17-177">O primeiro método exibe uma caixa de diálogo para selecionar um arquivo e passa seu nome de arquivo para o segundo método, que executa a descriptografia.</span><span class="sxs-lookup"><span data-stu-id="83d17-177">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="83d17-178">O `Decrypt` método faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="83d17-178">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="83d17-179">Cria um <xref:System.Security.Cryptography.RijndaelManaged> algoritmo simétrico para descriptografar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="83d17-179">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="83d17-180">Lê os primeiros oito bytes do <xref:System.IO.FileStream> do pacote criptografado em matrizes de bytes para obter os comprimentos de chave criptografada e o IV.</span><span class="sxs-lookup"><span data-stu-id="83d17-180">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="83d17-181">Extrai o IV e a chave do pacote de criptografia para matrizes de bytes.</span><span class="sxs-lookup"><span data-stu-id="83d17-181">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="83d17-182">Cria uma <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto para descriptografar o <xref:System.Security.Cryptography.RijndaelManaged> chave.</span><span class="sxs-lookup"><span data-stu-id="83d17-182">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5. <span data-ttu-id="83d17-183">Usa um <xref:System.Security.Cryptography.CryptoStream> objeto leia e descriptografar a seção de texto cifrado do <xref:System.IO.FileStream> criptografia de pacote, em blocos de bytes, no <xref:System.IO.FileStream> objeto para o arquivo descriptografado.</span><span class="sxs-lookup"><span data-stu-id="83d17-183">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="83d17-184">Quando isso for concluído, a descriptografia é concluída.</span><span class="sxs-lookup"><span data-stu-id="83d17-184">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="83d17-185">Adicione o seguinte código como o `Click` manipulador de eventos para o `Decrypt File` botão.</span><span class="sxs-lookup"><span data-stu-id="83d17-185">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="83d17-186">Adicione o seguinte `DecryptFile` método ao formulário.</span><span class="sxs-lookup"><span data-stu-id="83d17-186">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="83d17-187">Exportação de uma chave pública</span><span class="sxs-lookup"><span data-stu-id="83d17-187">Exporting a Public Key</span></span>  
 <span data-ttu-id="83d17-188">Essa tarefa salva a chave criada pelo `Create Keys` botão em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="83d17-188">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="83d17-189">Ele exporta somente os parâmetros públicos.</span><span class="sxs-lookup"><span data-stu-id="83d17-189">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="83d17-190">Essa tarefa simula o cenário de Alice dando Bob sua chave pública para que ele possa criptografar arquivos para ela.</span><span class="sxs-lookup"><span data-stu-id="83d17-190">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="83d17-191">Ele e outros que têm essa chave pública não poderá descriptografá-las, porque eles não têm o par de chave completo com parâmetros privados.</span><span class="sxs-lookup"><span data-stu-id="83d17-191">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="83d17-192">Adicione o seguinte código como o `Click` manipulador de eventos para o `Export Public Key` botão (`buttonExportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="83d17-192">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="83d17-193">Importando uma chave pública</span><span class="sxs-lookup"><span data-stu-id="83d17-193">Importing a Public Key</span></span>  
 <span data-ttu-id="83d17-194">Essa tarefa carrega a chave com parâmetros somente públicos, conforme criado pelo `Export Public Key` botão e, em seguida, define como o nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="83d17-194">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="83d17-195">Essa tarefa simula o cenário do Bob ao carregar a chave de Alice com apenas os parâmetros públicos para que ele pode criptografar arquivos para ela.</span><span class="sxs-lookup"><span data-stu-id="83d17-195">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="83d17-196">Adicione o seguinte código como o `Click` manipulador de eventos para o `Import Public Key` botão (`buttonImportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="83d17-196">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="83d17-197">Obtendo uma chave privada</span><span class="sxs-lookup"><span data-stu-id="83d17-197">Getting a Private Key</span></span>  
 <span data-ttu-id="83d17-198">Essa tarefa define o nome do contêiner de chave para o nome da chave criada usando o `Create Keys` botão.</span><span class="sxs-lookup"><span data-stu-id="83d17-198">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="83d17-199">O contêiner de chave contém o par de chave completo com parâmetros privados.</span><span class="sxs-lookup"><span data-stu-id="83d17-199">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="83d17-200">Essa tarefa simula o cenário de Alice usando sua chave privada para descriptografar arquivos criptografados por Bob.</span><span class="sxs-lookup"><span data-stu-id="83d17-200">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="83d17-201">Adicione o seguinte código como o `Click` manipulador de eventos para o `Get Private Key` botão (`buttonGetPrivateKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="83d17-201">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="83d17-202">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="83d17-202">Testing the Application</span></span>  
 <span data-ttu-id="83d17-203">Depois de criar o aplicativo, execute os seguintes cenários de teste.</span><span class="sxs-lookup"><span data-stu-id="83d17-203">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="83d17-204">Para criar chaves, criptografar e descriptografar</span><span class="sxs-lookup"><span data-stu-id="83d17-204">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="83d17-205">Clique no botão `Create Keys`.</span><span class="sxs-lookup"><span data-stu-id="83d17-205">Click the `Create Keys` button.</span></span> <span data-ttu-id="83d17-206">O rótulo exibe o nome da chave e mostra que é um par de chave completo.</span><span class="sxs-lookup"><span data-stu-id="83d17-206">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="83d17-207">Clique no botão `Export Public Key`.</span><span class="sxs-lookup"><span data-stu-id="83d17-207">Click the `Export Public Key` button.</span></span> <span data-ttu-id="83d17-208">Observe que os parâmetros de chave públicos a exportação não altera a chave atual.</span><span class="sxs-lookup"><span data-stu-id="83d17-208">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="83d17-209">Clique o `Encrypt File` botão e selecione um arquivo.</span><span class="sxs-lookup"><span data-stu-id="83d17-209">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="83d17-210">Clique o `Decrypt File` botão e selecione o arquivo criptografado apenas.</span><span class="sxs-lookup"><span data-stu-id="83d17-210">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="83d17-211">Examine o arquivo descriptografado apenas.</span><span class="sxs-lookup"><span data-stu-id="83d17-211">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="83d17-212">Feche o aplicativo e reiniciá-lo para testar ao recuperar contêineres de chave persistidos no próximo cenário.</span><span class="sxs-lookup"><span data-stu-id="83d17-212">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="83d17-213">Para criptografar usando a chave pública</span><span class="sxs-lookup"><span data-stu-id="83d17-213">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="83d17-214">Clique no botão `Import Public Key`.</span><span class="sxs-lookup"><span data-stu-id="83d17-214">Click the `Import Public Key` button.</span></span> <span data-ttu-id="83d17-215">O rótulo exibe o nome da chave e mostra que ele é público apenas.</span><span class="sxs-lookup"><span data-stu-id="83d17-215">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="83d17-216">Clique o `Encrypt File` botão e selecione um arquivo.</span><span class="sxs-lookup"><span data-stu-id="83d17-216">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="83d17-217">Clique o `Decrypt File` botão e selecione o arquivo criptografado apenas.</span><span class="sxs-lookup"><span data-stu-id="83d17-217">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="83d17-218">Isso irá falhar porque você deve ter a chave privada para descriptografar.</span><span class="sxs-lookup"><span data-stu-id="83d17-218">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="83d17-219">Este cenário demonstra tendo apenas a chave pública para criptografar um arquivo para outra pessoa.</span><span class="sxs-lookup"><span data-stu-id="83d17-219">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="83d17-220">Normalmente, essa pessoa seria lhe somente a chave pública e reter a chave privada para descriptografar.</span><span class="sxs-lookup"><span data-stu-id="83d17-220">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="83d17-221">Para descriptografar usando a chave privada</span><span class="sxs-lookup"><span data-stu-id="83d17-221">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="83d17-222">Clique no botão `Get Private Key`.</span><span class="sxs-lookup"><span data-stu-id="83d17-222">Click the `Get Private Key` button.</span></span> <span data-ttu-id="83d17-223">O rótulo exibe o nome da chave e mostra se ele é o par de chave completo.</span><span class="sxs-lookup"><span data-stu-id="83d17-223">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="83d17-224">Clique o `Decrypt File` botão e selecione o arquivo criptografado apenas.</span><span class="sxs-lookup"><span data-stu-id="83d17-224">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="83d17-225">Isso será bem-sucedida porque você tem o par de chave completo para descriptografar.</span><span class="sxs-lookup"><span data-stu-id="83d17-225">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d17-226">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83d17-226">See also</span></span>

- [<span data-ttu-id="83d17-227">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="83d17-227">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
