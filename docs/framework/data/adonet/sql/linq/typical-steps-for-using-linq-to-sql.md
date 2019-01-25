---
title: Etapas comuns de uso do LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: 32e81d08010f67b8eac19777a40826b18c440f83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548005"
---
# <a name="typical-steps-for-using-linq-to-sql"></a>Etapas comuns de uso do LINQ to SQL
Para implementar um aplicativo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], siga as etapas descritas mais adiante neste tópico. Observe que várias etapas são opcionais. É muito provável que você possa usar o modelo de objeto em seu estado padrão.  
  
 Para um início realmente rápido, use o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para criar o modelo de objeto e começar a codificar suas consultas.  
  
## <a name="creating-the-object-model"></a>Criando o modelo de objeto  
 A primeira etapa é criar um modelo de objeto a partir dos metadados de um banco de dados relacional existente. O modelo de objeto representa o banco de dados de acordo com a linguagem de programação do desenvolvedor. Para obter mais informações, consulte [o LINQ no modelo de objeto do SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1. Selecione uma ferramenta para criar o modelo.  
 Três ferramentas estão disponíveis para criar o modelo.  
  
-   O [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]  
  
     Esse designer fornece uma interface de usuário perfeita para criar um modelo de objeto a partir de um banco de dados existente. Essa ferramenta faz parte do IDE do Visual Studio e é ideal para bancos de dados de pequenos ou médios.  
  
-   A ferramenta de geração de código SQLMetal  
  
     Esse utilitário de linha de comando fornece um conjunto ligeiramente diferente de opções do [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. A modelagem de grandes bancos de dados é mais bem efetuada com essa ferramenta. Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
-   Um editor de código  
  
     Você pode escrever seu próprio código usando o editor de código do Visual Studio ou outro editor. Não recomendamos essa abordagem, que pode gerar erros, quando você tem um banco de dados e pode usar o [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] ou a ferramenta SQLMetal. Entretanto, o editor de códigos pode ser útil para refinar ou modificar o código que você já gerou usando outras ferramentas. Para obter mais informações, confira [Como: Personalizar Classes de entidade usando o Editor de código](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md).  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2. Selecione o tipo de código que você deseja gerar.  
  
-   Um C# ou arquivo de código de origem do Visual Basic para o mapeamento de atributo.  
  
     Você, em seguida, inclua esse arquivo de código em seu projeto do Visual Studio. Para obter mais informações, consulte [mapeamento baseado em atributo](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Um arquivo XML para mapeamento externo.  
  
     Usando essa abordagem, você pode manter os metadados de mapeamento fora de seu código de aplicativo. Para obter mais informações, consulte [mapeamento externo](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
    > [!NOTE]
    >  O [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] não oferece suporte à geração de arquivos de mapeamento externos. Você deve usar a ferramenta SQLMetal para implementar esse recurso.  
  
-   Um arquivo DBML, que você pode modificar antes de gerar um arquivo de código final.  
  
     Esse é um recurso avançado.  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3. Refine o arquivo de código para refletir as necessidades do seu aplicativo.  
 Para essa finalidade, você pode usar o [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] ou o editor de códigos.  
  
## <a name="using-the-object-model"></a>Usando o modelo de objeto  
 A ilustração a seguir mostra a relação entre o desenvolvedor e os dados em um cenário de duas camadas. Para outros cenários, consulte [de N camadas e aplicativos remotos com o LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md).  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 Agora que você tem o modelo de objeto, você descreve as solicitações de informações e manipula dados dentro desse modelo. Você pensa em termos de objetos e propriedades no seu modelo de objeto e não em termos de linhas e colunas do banco de dados. Você não lida diretamente com o banco de dados.  
  
 Quando você instrui [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a executar uma consulta que você descreveu ou chamada `SubmitChanges()` nos dados que você manipulou, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se comunica com o banco de dados no idioma do banco de dados.  
  
 A seguir estão etapas comuns de uso do modelo de objeto que você criou.  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1. Crie consultas para recuperar informações do banco de dados.  
 Para obter mais informações, consulte [conceitos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md) e [exemplos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md).  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2. Substitua comportamentos padrão para Insert, Update e Delete.  
 Esta etapa é opcional. Para obter mais informações, consulte [personalizando inserir, atualizar e excluir operações](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3. Defina opções apropriadas para detectar e relatar conflitos de simultaneidade.  
 Você pode deixar o modelo com seus valores padrão para manipular conflitos de simultaneidade, ou pode alterá-lo para atender aos seus propósitos. Para obter mais informações, confira [Como: Especificar quais membros são testados para conflitos de simultaneidade](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) e [como: Especificar quando exceções de simultaneidade são geradas](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4. Estabeleça uma hierarquia de herança.  
 Esta etapa é opcional. Para obter mais informações, consulte [suporte à herança](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5. Forneça uma interface de usuário apropriada.  
 Esta etapa é opcional, e depende de como o aplicativo será usado.  
  
### <a name="6-debug-and-test-your-application"></a>6. Depure e teste seu aplicativo.  
 Para obter mais informações, consulte [suporte de depuração](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="see-also"></a>Consulte também
- [Introdução](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
- [Criando o modelo de objeto](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Procedimentos armazenados](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
