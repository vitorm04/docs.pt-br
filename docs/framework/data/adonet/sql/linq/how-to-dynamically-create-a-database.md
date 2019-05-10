---
title: 'Como: criar um banco de dados dinamicamente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: e5d66b49782d5f26b6d487e655aca6fbd6bdfb1a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623860"
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="39157-102">Como: criar um banco de dados dinamicamente</span><span class="sxs-lookup"><span data-stu-id="39157-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="39157-103">No LINQ to SQL, um modelo de objeto é mapeado para um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="39157-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="39157-104">O mapeamento é habilitado usando o mapeamento baseado em atributo ou um arquivo de mapeamento externo para descrever a estrutura do banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="39157-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="39157-105">Em ambos os cenários, há informações suficientes sobre o banco de dados relacional para que você possa criar uma nova instância do banco de dados usando o método <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="39157-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="39157-106">O método <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> cria uma réplica do banco de dados somente para a extensão das informações codificadas no modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="39157-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="39157-107">Os arquivos de mapeamento e os atributos no modelo de objeto podem não codificar tudo sobre a estrutura de um banco de dados existente.</span><span class="sxs-lookup"><span data-stu-id="39157-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="39157-108">As informações de mapeamento não representam o conteúdo das funções definidas pelo usuário, dos procedimentos armazenados, dos gatilhos ou das restrições de verificação.</span><span class="sxs-lookup"><span data-stu-id="39157-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="39157-109">Esse comportamento é suficiente para vários bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="39157-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="39157-110">Você pode usar o método <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> em diversos cenários, especialmente se um provedor de dados conhecido como o Microsoft SQL Server 2008 estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="39157-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="39157-111">Os cenários comuns são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="39157-111">Typical scenarios include the following:</span></span>  
  
- <span data-ttu-id="39157-112">Você está criando um aplicativo que se instala automaticamente em um sistema de cliente.</span><span class="sxs-lookup"><span data-stu-id="39157-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
- <span data-ttu-id="39157-113">Você está criando um aplicativo cliente que precisa de um banco de dados local para salvar seu estado offline.</span><span class="sxs-lookup"><span data-stu-id="39157-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="39157-114">Você também pode usar o método <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> com o SQL Server usando um arquivo .mdf ou um nome de catálogo, dependendo da cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="39157-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> <span data-ttu-id="39157-115">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usa a cadeia de conexão para definir o banco de dados a ser criado e em qual servidor o banco de dados será criado.</span><span class="sxs-lookup"><span data-stu-id="39157-115">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39157-116">Sempre que possível, use a Segurança Integrada do Windows para se conectar ao banco de dados, de modo que não sejam necessárias senhas na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="39157-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39157-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39157-117">Example</span></span>  
 <span data-ttu-id="39157-118">O código a seguir fornece um exemplo de como criar um novo banco de dados chamado MyDVDs.mdf.</span><span class="sxs-lookup"><span data-stu-id="39157-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="39157-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39157-119">Example</span></span>  
 <span data-ttu-id="39157-120">Você pode usar o modelo de objeto para criar um banco de dados fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="39157-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="39157-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39157-121">Example</span></span>  
 <span data-ttu-id="39157-122">Ao criar um aplicativo que se instala automaticamente em um sistema de cliente, verifique se o banco de dados já existe e solte-o antes de criar um novo.</span><span class="sxs-lookup"><span data-stu-id="39157-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="39157-123">A classe <xref:System.Data.Linq.DataContext> fornece os métodos <xref:System.Data.Linq.DataContext.DatabaseExists%2A> e <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> para ajudar nesse processo.</span><span class="sxs-lookup"><span data-stu-id="39157-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="39157-124">O exemplo a seguir mostra uma maneira de implementar essa abordagem através desses métodos:</span><span class="sxs-lookup"><span data-stu-id="39157-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="39157-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39157-125">See also</span></span>

- [<span data-ttu-id="39157-126">Mapeamento baseado em atributos</span><span class="sxs-lookup"><span data-stu-id="39157-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [<span data-ttu-id="39157-127">Mapeamento Externo</span><span class="sxs-lookup"><span data-stu-id="39157-127">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [<span data-ttu-id="39157-128">Mapeamento de tipo CLR do SQL</span><span class="sxs-lookup"><span data-stu-id="39157-128">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [<span data-ttu-id="39157-129">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="39157-129">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="39157-130">Realizando e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="39157-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
