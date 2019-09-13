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
ms.openlocfilehash: ee6dafa8578c59d23908bf0e184091bb4ceaeb45
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895292"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="c29df-102">Passo a passo: criar um aplicativo criptográfico</span><span class="sxs-lookup"><span data-stu-id="c29df-102">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="c29df-103">Este tutorial demonstra como criptografar e descriptografar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c29df-103">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="c29df-104">Os exemplos de código são projetados para um aplicativo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c29df-104">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="c29df-105">Este aplicativo não demonstra cenários do mundo real, como o uso de cartões inteligentes.</span><span class="sxs-lookup"><span data-stu-id="c29df-105">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="c29df-106">Em vez disso, ele demonstra os conceitos básicos de criptografia e descriptografia.</span><span class="sxs-lookup"><span data-stu-id="c29df-106">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="c29df-107">Este tutorial usa as seguintes diretrizes para criptografia:</span><span class="sxs-lookup"><span data-stu-id="c29df-107">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="c29df-108">Use a <xref:System.Security.Cryptography.RijndaelManaged> classe, um algoritmo simétrico, para criptografar e descriptografar dados usando seu <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> automaticamente <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>gerado e.</span><span class="sxs-lookup"><span data-stu-id="c29df-108">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="c29df-109">Use o <xref:System.Security.Cryptography.RSACryptoServiceProvider>, um algoritmo assimétrico, para criptografar e descriptografar a chave para <xref:System.Security.Cryptography.RijndaelManaged>os dados criptografados pelo.</span><span class="sxs-lookup"><span data-stu-id="c29df-109">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="c29df-110">Os algoritmos assimétricos são mais bem usados para quantidades menores de dados, como uma chave.</span><span class="sxs-lookup"><span data-stu-id="c29df-110">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c29df-111">Se você quiser proteger os dados em seu computador em vez de trocar o conteúdo criptografado por outras pessoas, considere <xref:System.Security.Cryptography.ProtectedData> usar <xref:System.Security.Cryptography.ProtectedMemory> as classes ou.</span><span class="sxs-lookup"><span data-stu-id="c29df-111">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="c29df-112">A tabela a seguir resume as tarefas de criptografia neste tópico.</span><span class="sxs-lookup"><span data-stu-id="c29df-112">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="c29df-113">Tarefa</span><span class="sxs-lookup"><span data-stu-id="c29df-113">Task</span></span>|<span data-ttu-id="c29df-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c29df-114">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="c29df-115">Criando um aplicativo Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c29df-115">Creating a Windows Forms application</span></span>|<span data-ttu-id="c29df-116">Lista os controles que são necessários para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c29df-116">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="c29df-117">Declarando objetos globais</span><span class="sxs-lookup"><span data-stu-id="c29df-117">Declaring global objects</span></span>|<span data-ttu-id="c29df-118">Declara as variáveis de caminho da cadeia <xref:System.Security.Cryptography.CspParameters>de caracteres, <xref:System.Security.Cryptography.RSACryptoServiceProvider> o e o para <xref:System.Windows.Forms.Form> ter o contexto global da classe.</span><span class="sxs-lookup"><span data-stu-id="c29df-118">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="c29df-119">Criando uma chave assimétrica</span><span class="sxs-lookup"><span data-stu-id="c29df-119">Creating an asymmetric key</span></span>|<span data-ttu-id="c29df-120">Cria um par de valor de chave pública e privada assimétrica e atribui a ele um nome de contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="c29df-120">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="c29df-121">Criptografando um arquivo</span><span class="sxs-lookup"><span data-stu-id="c29df-121">Encrypting a file</span></span>|<span data-ttu-id="c29df-122">Exibe uma caixa de diálogo para selecionar um arquivo para criptografia e criptografa o arquivo.</span><span class="sxs-lookup"><span data-stu-id="c29df-122">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="c29df-123">Descriptografando um arquivo</span><span class="sxs-lookup"><span data-stu-id="c29df-123">Decrypting a file</span></span>|<span data-ttu-id="c29df-124">Exibe uma caixa de diálogo para selecionar um arquivo criptografado para descriptografia e descriptografar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="c29df-124">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="c29df-125">Obtendo uma chave privada</span><span class="sxs-lookup"><span data-stu-id="c29df-125">Getting a private key</span></span>|<span data-ttu-id="c29df-126">Obtém o par de chaves completo usando o nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="c29df-126">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="c29df-127">Exportando uma chave pública</span><span class="sxs-lookup"><span data-stu-id="c29df-127">Exporting a public key</span></span>|<span data-ttu-id="c29df-128">Salva a chave em um arquivo XML somente com parâmetros públicos.</span><span class="sxs-lookup"><span data-stu-id="c29df-128">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="c29df-129">Importando uma chave pública</span><span class="sxs-lookup"><span data-stu-id="c29df-129">Importing a public key</span></span>|<span data-ttu-id="c29df-130">Carrega a chave de um arquivo XML no contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="c29df-130">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="c29df-131">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="c29df-131">Testing the application</span></span>|<span data-ttu-id="c29df-132">Lista os procedimentos para testar este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c29df-132">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="c29df-133">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c29df-133">Prerequisites</span></span>  
 <span data-ttu-id="c29df-134">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="c29df-134">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="c29df-135">Referências aos namespaces <xref:System.IO> e <xref:System.Security.Cryptography>.</span><span class="sxs-lookup"><span data-stu-id="c29df-135">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="c29df-136">Criando um aplicativo Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c29df-136">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="c29df-137">A maioria dos exemplos de código neste passo a passos é projetada para ser manipuladores de eventos para controles de botão.</span><span class="sxs-lookup"><span data-stu-id="c29df-137">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="c29df-138">A tabela a seguir lista os controles necessários para o aplicativo de exemplo e seus nomes necessários para corresponder aos exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="c29df-138">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="c29df-139">Controle</span><span class="sxs-lookup"><span data-stu-id="c29df-139">Control</span></span>|<span data-ttu-id="c29df-140">Nome</span><span class="sxs-lookup"><span data-stu-id="c29df-140">Name</span></span>|<span data-ttu-id="c29df-141">Propriedade Text (conforme necessário)</span><span class="sxs-lookup"><span data-stu-id="c29df-141">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="c29df-142">Criptografar arquivo</span><span class="sxs-lookup"><span data-stu-id="c29df-142">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="c29df-143">Descriptografar arquivo</span><span class="sxs-lookup"><span data-stu-id="c29df-143">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="c29df-144">Criar chaves</span><span class="sxs-lookup"><span data-stu-id="c29df-144">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="c29df-145">Exportar chave pública</span><span class="sxs-lookup"><span data-stu-id="c29df-145">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="c29df-146">Importar chave pública</span><span class="sxs-lookup"><span data-stu-id="c29df-146">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="c29df-147">Obter chave privada</span><span class="sxs-lookup"><span data-stu-id="c29df-147">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="c29df-148">Chave não definida</span><span class="sxs-lookup"><span data-stu-id="c29df-148">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="c29df-149">Clique duas vezes nos botões no designer do Visual Studio para criar seus manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="c29df-149">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="c29df-150">Declarando objetos globais</span><span class="sxs-lookup"><span data-stu-id="c29df-150">Declaring Global Objects</span></span>  
 <span data-ttu-id="c29df-151">Adicione o código a seguir ao construtor do formulário.</span><span class="sxs-lookup"><span data-stu-id="c29df-151">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="c29df-152">Edite as variáveis de cadeia de caracteres para seu ambiente e preferências.</span><span class="sxs-lookup"><span data-stu-id="c29df-152">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="c29df-153">Criando uma chave assimétrica</span><span class="sxs-lookup"><span data-stu-id="c29df-153">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="c29df-154">Essa tarefa cria uma chave assimétrica que criptografa e descriptografa a <xref:System.Security.Cryptography.RijndaelManaged> chave.</span><span class="sxs-lookup"><span data-stu-id="c29df-154">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="c29df-155">Essa chave foi usada para criptografar o conteúdo e exibe o nome do contêiner de chave no controle rótulo.</span><span class="sxs-lookup"><span data-stu-id="c29df-155">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="c29df-156">Adicione o código a seguir como `Click` o manipulador de eventos `Create Keys` para o`buttonCreateAsmKeys_Click`botão ().</span><span class="sxs-lookup"><span data-stu-id="c29df-156">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="c29df-157">Criptografando um arquivo</span><span class="sxs-lookup"><span data-stu-id="c29df-157">Encrypting a File</span></span>  
 <span data-ttu-id="c29df-158">Essa tarefa envolve dois métodos: o método manipulador de eventos para `Encrypt File` o botão`buttonEncryptFile_Click`() e `EncryptFile` o método.</span><span class="sxs-lookup"><span data-stu-id="c29df-158">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="c29df-159">O primeiro método exibe uma caixa de diálogo para selecionar um arquivo e passa o nome do arquivo para o segundo método, que executa a criptografia.</span><span class="sxs-lookup"><span data-stu-id="c29df-159">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="c29df-160">O conteúdo criptografado, a chave e o IV são todos salvos <xref:System.IO.FileStream>em um, que é conhecido como o pacote de criptografia.</span><span class="sxs-lookup"><span data-stu-id="c29df-160">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="c29df-161">O `EncryptFile` método faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c29df-161">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="c29df-162">Cria um <xref:System.Security.Cryptography.RijndaelManaged> algoritmo simétrico para criptografar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c29df-162">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="c29df-163">Cria um <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto para criptografar <xref:System.Security.Cryptography.RijndaelManaged> a chave.</span><span class="sxs-lookup"><span data-stu-id="c29df-163">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3. <span data-ttu-id="c29df-164">Usa um <xref:System.Security.Cryptography.CryptoStream> objeto para ler e criptografar <xref:System.IO.FileStream> o do arquivo de origem, em blocos de bytes, em um <xref:System.IO.FileStream> objeto de destino para o arquivo criptografado.</span><span class="sxs-lookup"><span data-stu-id="c29df-164">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="c29df-165">Determina os comprimentos da chave criptografada e IV e cria matrizes de bytes de seus valores de comprimento.</span><span class="sxs-lookup"><span data-stu-id="c29df-165">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="c29df-166">Grava a chave, o IV e seus valores de comprimento para o pacote criptografado.</span><span class="sxs-lookup"><span data-stu-id="c29df-166">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="c29df-167">O pacote de criptografia usa o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="c29df-167">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="c29df-168">Comprimento da chave, bytes 0-3</span><span class="sxs-lookup"><span data-stu-id="c29df-168">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="c29df-169">Comprimento de IV, bytes 4-7</span><span class="sxs-lookup"><span data-stu-id="c29df-169">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="c29df-170">Chave criptografada</span><span class="sxs-lookup"><span data-stu-id="c29df-170">Encrypted key</span></span>  
  
- <span data-ttu-id="c29df-171">IV</span><span class="sxs-lookup"><span data-stu-id="c29df-171">IV</span></span>  
  
- <span data-ttu-id="c29df-172">Texto cifrado</span><span class="sxs-lookup"><span data-stu-id="c29df-172">Cipher text</span></span>  
  
 <span data-ttu-id="c29df-173">Você pode usar os comprimentos da chave e do IV para determinar os pontos de partida e os comprimentos de todas as partes do pacote de criptografia, que podem ser usados para descriptografar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="c29df-173">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="c29df-174">Adicione o código a seguir como `Click` o manipulador de eventos `Encrypt File` para o`buttonEncryptFile_Click`botão ().</span><span class="sxs-lookup"><span data-stu-id="c29df-174">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="c29df-175">Adicione o seguinte `EncryptFile` método ao formulário.</span><span class="sxs-lookup"><span data-stu-id="c29df-175">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="c29df-176">Descriptografando um arquivo</span><span class="sxs-lookup"><span data-stu-id="c29df-176">Decrypting a File</span></span>  
 <span data-ttu-id="c29df-177">Essa tarefa envolve dois métodos, o método manipulador de eventos para `Decrypt File` o botão`buttonDecryptFile_Click`() e o `DecryptFile` método.</span><span class="sxs-lookup"><span data-stu-id="c29df-177">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="c29df-178">O primeiro método exibe uma caixa de diálogo para selecionar um arquivo e passa seu nome de arquivo para o segundo método, que executa a descriptografia.</span><span class="sxs-lookup"><span data-stu-id="c29df-178">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="c29df-179">O `Decrypt` método faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c29df-179">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="c29df-180">Cria um <xref:System.Security.Cryptography.RijndaelManaged> algoritmo simétrico para descriptografar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c29df-180">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="c29df-181">Lê os primeiros oito bytes do <xref:System.IO.FileStream> pacote criptografado em matrizes de bytes para obter os comprimentos da chave criptografada e o IV.</span><span class="sxs-lookup"><span data-stu-id="c29df-181">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="c29df-182">Extrai a chave e o IV do pacote de criptografia em matrizes de bytes.</span><span class="sxs-lookup"><span data-stu-id="c29df-182">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="c29df-183">Cria um <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto para descriptografar a <xref:System.Security.Cryptography.RijndaelManaged> chave.</span><span class="sxs-lookup"><span data-stu-id="c29df-183">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5. <span data-ttu-id="c29df-184">Usa um <xref:System.Security.Cryptography.CryptoStream> objeto para ler e descriptografar a seção <xref:System.IO.FileStream> de texto cifrado do pacote de criptografia, em blocos <xref:System.IO.FileStream> de bytes, no objeto do arquivo descriptografado.</span><span class="sxs-lookup"><span data-stu-id="c29df-184">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="c29df-185">Quando isso for concluído, a descriptografia será concluída.</span><span class="sxs-lookup"><span data-stu-id="c29df-185">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="c29df-186">Adicione o código a seguir como `Click` o manipulador de eventos `Decrypt File` para o botão.</span><span class="sxs-lookup"><span data-stu-id="c29df-186">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="c29df-187">Adicione o seguinte `DecryptFile` método ao formulário.</span><span class="sxs-lookup"><span data-stu-id="c29df-187">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="c29df-188">Exportando uma chave pública</span><span class="sxs-lookup"><span data-stu-id="c29df-188">Exporting a Public Key</span></span>  
 <span data-ttu-id="c29df-189">Essa tarefa salva a chave criada pelo `Create Keys` botão em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c29df-189">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="c29df-190">Ele exporta apenas os parâmetros públicos.</span><span class="sxs-lookup"><span data-stu-id="c29df-190">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="c29df-191">Essa tarefa simula o cenário de Alice dando a Bob sua chave pública para que ele possa criptografar arquivos.</span><span class="sxs-lookup"><span data-stu-id="c29df-191">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="c29df-192">Ele e outros que tenham essa chave pública não poderão descriptografá-los porque não têm o par de chaves completo com parâmetros privados.</span><span class="sxs-lookup"><span data-stu-id="c29df-192">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="c29df-193">Adicione o código a seguir como `Click` o manipulador de eventos `Export Public Key` para o`buttonExportPublicKey_Click`botão ().</span><span class="sxs-lookup"><span data-stu-id="c29df-193">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="c29df-194">Importando uma chave pública</span><span class="sxs-lookup"><span data-stu-id="c29df-194">Importing a Public Key</span></span>  
 <span data-ttu-id="c29df-195">Essa tarefa carrega a chave somente com parâmetros públicos, conforme criado pelo `Export Public Key` botão e o define como o nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="c29df-195">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="c29df-196">Esta tarefa simula o cenário de Bob carregando a chave de Alice com apenas parâmetros públicos, portanto, ele pode criptografar arquivos.</span><span class="sxs-lookup"><span data-stu-id="c29df-196">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="c29df-197">Adicione o código a seguir como `Click` o manipulador de eventos `Import Public Key` para o`buttonImportPublicKey_Click`botão ().</span><span class="sxs-lookup"><span data-stu-id="c29df-197">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="c29df-198">Obtendo uma chave privada</span><span class="sxs-lookup"><span data-stu-id="c29df-198">Getting a Private Key</span></span>  
 <span data-ttu-id="c29df-199">Essa tarefa define o nome do contêiner de chave como o nome da chave criada usando o `Create Keys` botão.</span><span class="sxs-lookup"><span data-stu-id="c29df-199">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="c29df-200">O contêiner de chave conterá o par de chaves completo com parâmetros privados.</span><span class="sxs-lookup"><span data-stu-id="c29df-200">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="c29df-201">Esta tarefa simula o cenário de Alice usando sua chave privada para descriptografar arquivos criptografados por Bob.</span><span class="sxs-lookup"><span data-stu-id="c29df-201">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="c29df-202">Adicione o código a seguir como `Click` o manipulador de eventos `Get Private Key` para o`buttonGetPrivateKey_Click`botão ().</span><span class="sxs-lookup"><span data-stu-id="c29df-202">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="c29df-203">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="c29df-203">Testing the Application</span></span>  
 <span data-ttu-id="c29df-204">Depois de criar o aplicativo, execute os seguintes cenários de teste.</span><span class="sxs-lookup"><span data-stu-id="c29df-204">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="c29df-205">Para criar chaves, criptografar e descriptografar</span><span class="sxs-lookup"><span data-stu-id="c29df-205">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="c29df-206">Clique no botão `Create Keys`.</span><span class="sxs-lookup"><span data-stu-id="c29df-206">Click the `Create Keys` button.</span></span> <span data-ttu-id="c29df-207">O rótulo exibe o nome da chave e mostra que ele é um par de chaves completo.</span><span class="sxs-lookup"><span data-stu-id="c29df-207">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="c29df-208">Clique no botão `Export Public Key`.</span><span class="sxs-lookup"><span data-stu-id="c29df-208">Click the `Export Public Key` button.</span></span> <span data-ttu-id="c29df-209">Observe que a exportação dos parâmetros de chave pública não altera a chave atual.</span><span class="sxs-lookup"><span data-stu-id="c29df-209">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="c29df-210">Clique no `Encrypt File` botão e selecione um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c29df-210">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="c29df-211">Clique no `Decrypt File` botão e selecione o arquivo que acabou de ser criptografado.</span><span class="sxs-lookup"><span data-stu-id="c29df-211">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="c29df-212">Examine o arquivo apenas descriptografado.</span><span class="sxs-lookup"><span data-stu-id="c29df-212">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="c29df-213">Feche o aplicativo e reinicie-o para testar a recuperação de contêineres de chave persistentes no próximo cenário.</span><span class="sxs-lookup"><span data-stu-id="c29df-213">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="c29df-214">Para criptografar usando a chave pública</span><span class="sxs-lookup"><span data-stu-id="c29df-214">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="c29df-215">Clique no botão `Import Public Key`.</span><span class="sxs-lookup"><span data-stu-id="c29df-215">Click the `Import Public Key` button.</span></span> <span data-ttu-id="c29df-216">O rótulo exibe o nome da chave e mostra que ele é somente público.</span><span class="sxs-lookup"><span data-stu-id="c29df-216">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="c29df-217">Clique no `Encrypt File` botão e selecione um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c29df-217">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="c29df-218">Clique no `Decrypt File` botão e selecione o arquivo que acabou de ser criptografado.</span><span class="sxs-lookup"><span data-stu-id="c29df-218">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="c29df-219">Isso irá falhar porque você deve ter a chave privada para descriptografar.</span><span class="sxs-lookup"><span data-stu-id="c29df-219">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="c29df-220">Este cenário demonstra como ter apenas a chave pública para criptografar um arquivo para outra pessoa.</span><span class="sxs-lookup"><span data-stu-id="c29df-220">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="c29df-221">Normalmente, essa pessoa daria apenas a chave pública e a chave privada para a descriptografia.</span><span class="sxs-lookup"><span data-stu-id="c29df-221">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="c29df-222">Para descriptografar usando a chave privada</span><span class="sxs-lookup"><span data-stu-id="c29df-222">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="c29df-223">Clique no botão `Get Private Key`.</span><span class="sxs-lookup"><span data-stu-id="c29df-223">Click the `Get Private Key` button.</span></span> <span data-ttu-id="c29df-224">O rótulo exibe o nome da chave e mostra se ele é o par de chaves completo.</span><span class="sxs-lookup"><span data-stu-id="c29df-224">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="c29df-225">Clique no `Decrypt File` botão e selecione o arquivo que acabou de ser criptografado.</span><span class="sxs-lookup"><span data-stu-id="c29df-225">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="c29df-226">Isso será bem-sucedido porque você tem o par de chaves completo a ser descriptografado.</span><span class="sxs-lookup"><span data-stu-id="c29df-226">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c29df-227">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c29df-227">See also</span></span>

- [<span data-ttu-id="c29df-228">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="c29df-228">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
