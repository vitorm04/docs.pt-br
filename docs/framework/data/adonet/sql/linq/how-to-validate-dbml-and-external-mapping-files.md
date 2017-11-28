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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c4c17b41f9bee3ce43b7627343fec2b5a69dbba8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Como: Validar DBML e arquivos de mapeamento externos
Os arquivos de mapeamento externos e os arquivos .dbml que você altera devem ser validadas contra suas respectivas definições de esquema. Este tópico fornece os usuários de [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] com as etapas para implementar o processo de validação.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a>Para validar um .dbml ou um arquivo XML  
  
1.  No Visual Studio **arquivo** , aponte para **abrir**e, em seguida, clique em **arquivo**.  
  
2.  No **abrir arquivo** caixa de diálogo, clique o dbml ou o arquivo de mapeamento de XML que você deseja validar.  
  
     O arquivo é aberto no **Editor XML**.  
  
3.  Clique com botão direito a janela e, em seguida, clique em **propriedades**.  
  
4.  No **propriedades** janela, clique no botão de reticências para o **esquemas** propriedade.  
  
     O **esquemas XML** caixa de diálogo é aberta.  
  
5.  Observe a definição apropriada do esquema para sua finalidade.  
  
    -   DbmlSchema.xsd é a definição de esquema para validar um arquivo. dbml. Para obter mais informações, consulte [geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   LinqToSqlMapping.xsd é a definição de esquema para validar um arquivo de mapeamento externo XML. Para obter mais informações, consulte [mapeamento externo](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
6.  No **Use** coluna da linha de definição de esquema desejado, clique para abrir a caixa de lista suspensa e, em seguida, clique em **utilizam este esquema**.  
  
     O arquivo de definição de esquema agora está associado com seu arquivo de mapeamento de DBML ou XML.  
  
     Certifique-se de que nenhuma outra definição de esquema está selecionada.  
  
7.  Sobre o **exibição** menu, clique em **lista de erros**.  
  
     Determine se os erros, avisos, ou mensagens foram gerados. Caso contrário, o arquivo XML é válido na definição de esquema.  
  
## <a name="alternate-method-for-supplying-schema-definition"></a>Método alternativo para fornecer a definição de esquema  
 Se por alguma razão. o XSD apropriado arquivo não aparecer a **esquemas XML** caixa de diálogo, você pode baixar o arquivo. xsd de um tópico da Ajuda. As etapas a seguir ajudam você a salvar o arquivo baixado no formato Unicode exigido pelo editor de [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] .  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Para copiar uma definição de esquema partir de um tópico da Ajuda  
  
1.  Localize o tópico da Ajuda que contém a definição de esquema conforme descrito anteriormente neste tópico.  
  
    -   Arquivos dbml, consulte [geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   Para arquivos de mapeamento externos, consulte [mapeamento externo](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
2.  Clique em **Copiar código** para copiar o arquivo de código para a área de transferência.  
  
3.  Inicie o Bloco De Notas para criar um novo arquivo.  
  
4.  Cole o código da área de transferência no arquivo do Bloco De Notas.  
  
5.  Sobre o bloco de notas **arquivo** menu, clique em **Salvar como**.  
  
6.  No **codificação** selecione **Unicode**.  
  
    > [!IMPORTANT]
    >  Essa seleção garante que o marcador de bytes ordem Unicode-16 (`FFFE`) prepended para o arquivo de texto.  
  
7.  No **nome de arquivo** caixa, crie um nome de arquivo com uma extensão. xsd.  
  
## <a name="see-also"></a>Consulte também  
 [Referência](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
