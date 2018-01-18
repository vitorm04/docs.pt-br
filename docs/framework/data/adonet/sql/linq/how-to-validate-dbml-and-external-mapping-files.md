---
title: 'Como: Validar DBML e arquivos de mapeamento externos'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7724586c33c19654c3657a5a4604a3c74f2c8756
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="9cb51-102">Como: Validar DBML e arquivos de mapeamento externos</span><span class="sxs-lookup"><span data-stu-id="9cb51-102">How to: Validate DBML and External Mapping Files</span></span>
<span data-ttu-id="9cb51-103">Os arquivos de mapeamento externos e os arquivos .dbml que você altera devem ser validadas contra suas respectivas definições de esquema.</span><span class="sxs-lookup"><span data-stu-id="9cb51-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="9cb51-104">Este tópico fornece os usuários de [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] com as etapas para implementar o processo de validação.</span><span class="sxs-lookup"><span data-stu-id="9cb51-104">This topic provides [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] users with the steps to implement the validation process.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="9cb51-105">Para validar um .dbml ou um arquivo XML</span><span class="sxs-lookup"><span data-stu-id="9cb51-105">To validate a .dbml or XML file</span></span>  
  
1.  <span data-ttu-id="9cb51-106">No Visual Studio **arquivo** , aponte para **abrir**e, em seguida, clique em **arquivo**.</span><span class="sxs-lookup"><span data-stu-id="9cb51-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="9cb51-107">No **abrir arquivo** caixa de diálogo, clique o dbml ou o arquivo de mapeamento de XML que você deseja validar.</span><span class="sxs-lookup"><span data-stu-id="9cb51-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>  
  
     <span data-ttu-id="9cb51-108">O arquivo é aberto no **Editor XML**.</span><span class="sxs-lookup"><span data-stu-id="9cb51-108">The file opens in the **XML Editor**.</span></span>  
  
3.  <span data-ttu-id="9cb51-109">Clique com botão direito a janela e, em seguida, clique em **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="9cb51-109">Right-click the window, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="9cb51-110">No **propriedades** janela, clique no botão de reticências para o **esquemas** propriedade.</span><span class="sxs-lookup"><span data-stu-id="9cb51-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>  
  
     <span data-ttu-id="9cb51-111">O **esquemas XML** caixa de diálogo é aberta.</span><span class="sxs-lookup"><span data-stu-id="9cb51-111">The **XML Schemas** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="9cb51-112">Observe a definição apropriada do esquema para sua finalidade.</span><span class="sxs-lookup"><span data-stu-id="9cb51-112">Note the appropriate schema definition for your purpose.</span></span>  
  
    -   <span data-ttu-id="9cb51-113">DbmlSchema.xsd é a definição de esquema para validar um arquivo. dbml.</span><span class="sxs-lookup"><span data-stu-id="9cb51-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="9cb51-114">Para obter mais informações, consulte [geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9cb51-114">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="9cb51-115">LinqToSqlMapping.xsd é a definição de esquema para validar um arquivo de mapeamento externo XML.</span><span class="sxs-lookup"><span data-stu-id="9cb51-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="9cb51-116">Para obter mais informações, consulte [mapeamento externo](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="9cb51-116">For more information, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
6.  <span data-ttu-id="9cb51-117">No **Use** coluna da linha de definição de esquema desejado, clique para abrir a caixa de lista suspensa e, em seguida, clique em **utilizam este esquema**.</span><span class="sxs-lookup"><span data-stu-id="9cb51-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>  
  
     <span data-ttu-id="9cb51-118">O arquivo de definição de esquema agora está associado com seu arquivo de mapeamento de DBML ou XML.</span><span class="sxs-lookup"><span data-stu-id="9cb51-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>  
  
     <span data-ttu-id="9cb51-119">Certifique-se de que nenhuma outra definição de esquema está selecionada.</span><span class="sxs-lookup"><span data-stu-id="9cb51-119">Make sure no other schema definitions are selected.</span></span>  
  
7.  <span data-ttu-id="9cb51-120">Sobre o **exibição** menu, clique em **lista de erros**.</span><span class="sxs-lookup"><span data-stu-id="9cb51-120">On the **View** menu, click **Error List**.</span></span>  
  
     <span data-ttu-id="9cb51-121">Determine se os erros, avisos, ou mensagens foram gerados.</span><span class="sxs-lookup"><span data-stu-id="9cb51-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="9cb51-122">Caso contrário, o arquivo XML é válido na definição de esquema.</span><span class="sxs-lookup"><span data-stu-id="9cb51-122">If not, the XML file is valid against the schema definition.</span></span>  
  
## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="9cb51-123">Método alternativo para fornecer a definição de esquema</span><span class="sxs-lookup"><span data-stu-id="9cb51-123">Alternate Method for Supplying Schema Definition</span></span>  
 <span data-ttu-id="9cb51-124">Se por alguma razão. o XSD apropriado arquivo não aparecer a **esquemas XML** caixa de diálogo, você pode baixar o arquivo. xsd de um tópico da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="9cb51-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="9cb51-125">As etapas a seguir ajudam você a salvar o arquivo baixado no formato Unicode exigido pelo editor de [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9cb51-125">The following steps help you save the downloaded file in the Unicode format required by the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] XML Editor.</span></span>  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="9cb51-126">Para copiar uma definição de esquema partir de um tópico da Ajuda</span><span class="sxs-lookup"><span data-stu-id="9cb51-126">To copy a schema definition file from a Help topic</span></span>  
  
1.  <span data-ttu-id="9cb51-127">Localize o tópico da Ajuda que contém a definição de esquema conforme descrito anteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="9cb51-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="9cb51-128">Arquivos dbml, consulte [geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9cb51-128">For .dbml files, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="9cb51-129">Para arquivos de mapeamento externos, consulte [mapeamento externo](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="9cb51-129">For external mapping files, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
2.  <span data-ttu-id="9cb51-130">Clique em **Copiar código** para copiar o arquivo de código para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="9cb51-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="9cb51-131">Inicie o Bloco De Notas para criar um novo arquivo.</span><span class="sxs-lookup"><span data-stu-id="9cb51-131">Start Notepad to create a new file.</span></span>  
  
4.  <span data-ttu-id="9cb51-132">Cole o código da área de transferência no arquivo do Bloco De Notas.</span><span class="sxs-lookup"><span data-stu-id="9cb51-132">Paste the code from the clipboard into Notepad file.</span></span>  
  
5.  <span data-ttu-id="9cb51-133">Sobre o bloco de notas **arquivo** menu, clique em **Salvar como**.</span><span class="sxs-lookup"><span data-stu-id="9cb51-133">On the Notepad **File** menu, click **Save As**.</span></span>  
  
6.  <span data-ttu-id="9cb51-134">No **codificação** selecione **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="9cb51-134">In the **Encoding** box, select **Unicode**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9cb51-135">Essa seleção garante que o marcador de bytes ordem Unicode-16 (`FFFE`) prepended para o arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="9cb51-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>  
  
7.  <span data-ttu-id="9cb51-136">No **nome de arquivo** caixa, crie um nome de arquivo com uma extensão. xsd.</span><span class="sxs-lookup"><span data-stu-id="9cb51-136">In the **File name** box, create a file name with an .xsd extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb51-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cb51-137">See Also</span></span>  
 [<span data-ttu-id="9cb51-138">Referência</span><span class="sxs-lookup"><span data-stu-id="9cb51-138">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
