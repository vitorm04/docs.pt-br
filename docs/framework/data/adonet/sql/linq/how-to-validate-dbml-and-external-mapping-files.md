---
title: 'Como: validar DBML e arquivos de mapeamento externos'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 212d65dfe998b825dd40e564756083ed685dff6f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041137"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a>Como: validar DBML e arquivos de mapeamento externos

Os arquivos de mapeamento externos e os arquivos .dbml que você altera devem ser validadas contra suas respectivas definições de esquema. Este tópico fornece aos usuários do Visual Studio as etapas para implementar o processo de validação.

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

### <a name="to-validate-a-dbml-or-xml-file"></a>Para validar um .dbml ou um arquivo XML

1. No menu **arquivo** do Visual Studio, aponte para **abrir**e clique em **arquivo**.

2. Na caixa de diálogo **Abrir arquivo** , clique no arquivo de mapeamento. dbml ou XML que você deseja validar.

    O arquivo é aberto no **Editor de XML**.

3. Clique com o botão direito do mouse na janela e clique em **Propriedades**.

4. Na janela **Propriedades** , clique nas reticências da propriedade **esquemas** .

    A caixa de diálogo **esquemas XML** é aberta.

5. Observe a definição apropriada do esquema para sua finalidade.

    - DbmlSchema.xsd é a definição de esquema para validar um arquivo. dbml. Para obter mais informações, consulte [geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).

    - LinqToSqlMapping.xsd é a definição de esquema para validar um arquivo de mapeamento externo XML. Para obter mais informações, consulte [mapeamento externo](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).

6. Na coluna **usar** da linha de definição de esquema desejada, clique para abrir a caixa suspensa e, em seguida, clique em **usar este esquema**.

    O arquivo de definição de esquema agora está associado com seu arquivo de mapeamento de DBML ou XML.

    Certifique-se de que nenhuma outra definição de esquema está selecionada.

7. No menu **Exibir** , clique em **lista de erros**.

    Determine se os erros, avisos, ou mensagens foram gerados. Caso contrário, o arquivo XML é válido na definição de esquema.

## <a name="alternate-method-for-supplying-schema-definition"></a>Método alternativo para fornecer a definição de esquema

Se por algum motivo o arquivo. xsd apropriado não aparecer na caixa de diálogo **esquemas XML** , você poderá baixar o arquivo. xsd de um tópico da ajuda. As etapas a seguir ajudam a salvar o arquivo baixado no formato Unicode exigido pelo editor de XML do Visual Studio.

#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a>Para copiar uma definição de esquema partir de um tópico da Ajuda

1. Localize o tópico da Ajuda que contém a definição de esquema conforme descrito anteriormente neste tópico.

    - Para arquivos. dbml, consulte [geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).

    - Para arquivos de mapeamento externos, consulte [mapeamento externo](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).

2. Clique em **copiar código** para copiar o arquivo de código para a área de transferência.

3. Inicie o Bloco De Notas para criar um novo arquivo.

4. Cole o código da área de transferência no arquivo do Bloco De Notas.

5. No menu **arquivo** do bloco de notas, clique em **salvar como**.

6. Na caixa **codificação** , selecione **Unicode**.

    > [!IMPORTANT]
    > Essa seleção garante que o marcador de bytes ordem Unicode-16 (`FFFE`) prepended para o arquivo de texto.

7. Na caixa **nome do arquivo** , crie um nome de arquivo com uma extensão. xsd.

## <a name="see-also"></a>Consulte também

- [Referência](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
