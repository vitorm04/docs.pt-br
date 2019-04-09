---
title: 'Como: validar DBML e arquivos de mapeamento externos'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: b01bcf98bba185b7a4b1802f470a585371980177
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078727"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Como: validar DBML e arquivos de mapeamento externos
Os arquivos de mapeamento externos e os arquivos .dbml que você altera devem ser validadas contra suas respectivas definições de esquema. Este tópico fornece os usuários do Visual Studio com as etapas para implementar o processo de validação.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a>Para validar um .dbml ou um arquivo XML  
  
1.  No Visual Studio **arquivo** , aponte para **abra**e, em seguida, clique em **arquivo**.  
  
2.  No **abrir arquivo** caixa de diálogo, clique em. dbml ou do arquivo de mapeamento de XML que você deseja validar.  
  
     O arquivo é aberto na **Editor de XML**.  
  
3.  A janela com o botão direito e, em seguida, clique em **propriedades**.  
  
4.  No **propriedades** janela, clique no botão de reticências para o **esquemas** propriedade.  
  
     O **esquemas XML** caixa de diálogo é aberta.  
  
5.  Observe a definição apropriada do esquema para sua finalidade.  
  
    -   DbmlSchema.xsd é a definição de esquema para validar um arquivo. dbml. Para obter mais informações, consulte [geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   LinqToSqlMapping.xsd é a definição de esquema para validar um arquivo de mapeamento externo XML. Para obter mais informações, consulte [mapeamento externo](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
6.  No **uso** coluna da linha de definição de esquema desejado, clique para abrir a caixa de lista suspensa e, em seguida, clique em **usar este esquema**.  
  
     O arquivo de definição de esquema agora está associado com seu arquivo de mapeamento de DBML ou XML.  
  
     Certifique-se de que nenhuma outra definição de esquema está selecionada.  
  
7.  Sobre o **modo de exibição** menu, clique em **lista de erros**.  
  
     Determine se os erros, avisos, ou mensagens foram gerados. Caso contrário, o arquivo XML é válido na definição de esquema.  
  
## <a name="alternate-method-for-supplying-schema-definition"></a>Método alternativo para fornecer a definição de esquema  
 Se por algum motivo a. xsd apropriado arquivo não aparecer na **esquemas XML** caixa de diálogo, você pode baixar o arquivo. xsd de um tópico de Ajuda. As etapas a seguir o ajudarão a salvar o arquivo baixado no formato Unicode exigido pelo Editor de XML do Visual Studio.  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Para copiar uma definição de esquema partir de um tópico da Ajuda  
  
1.  Localize o tópico da Ajuda que contém a definição de esquema conforme descrito anteriormente neste tópico.  
  
    -   Para arquivos. dbml, consulte [geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
    -   Para arquivos de mapeamento externo, consulte [mapeamento externo](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
2.  Clique em **Copiar código** para copiar o arquivo de código para a área de transferência.  
  
3.  Inicie o Bloco De Notas para criar um novo arquivo.  
  
4.  Cole o código da área de transferência no arquivo do Bloco De Notas.  
  
5.  Sobre o bloco de notas **arquivo** menu, clique em **Salvar como**.  
  
6.  No **Encoding** caixa, selecione **Unicode**.  
  
    > [!IMPORTANT]
    >  Essa seleção garante que o marcador de bytes ordem Unicode-16 (`FFFE`) prepended para o arquivo de texto.  
  
7.  No **nome do arquivo** caixa, crie um nome de arquivo com uma extensão. xsd.  
  
## <a name="see-also"></a>Consulte também

- [Referência](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
