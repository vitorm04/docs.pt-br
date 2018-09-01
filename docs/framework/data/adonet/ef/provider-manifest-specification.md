---
title: Especificação do manifesto do provedor
ms.date: 03/30/2017
ms.assetid: bb450b47-8951-4f99-9350-26f05a4d4e46
ms.openlocfilehash: 9875f0ce8d7b10532d7545c05d58ab43146120f0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387296"
---
# <a name="provider-manifest-specification"></a><span data-ttu-id="b2d80-102">Especificação do manifesto do provedor</span><span class="sxs-lookup"><span data-stu-id="b2d80-102">Provider Manifest Specification</span></span>
<span data-ttu-id="b2d80-103">Esta seção discute como um provedor de armazenamento de dados pode suportar os tipos e funções no armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="b2d80-103">This section discusses how a data store provider can support the types and functions in the data store.</span></span>  
  
 <span data-ttu-id="b2d80-104">Os serviços de entidade operam independentemente de um provedor específico de armazenamento de dados ainda permitir que que um provedor de dados defina explicitamente como modelos, os mapeamentos, e as consultas interagem com um armazenamento de dados subjacentes.</span><span class="sxs-lookup"><span data-stu-id="b2d80-104">Entity Services operates independently of a specific data store provider yet still allows a data provider to explicitly define how models, mappings, and queries interact with an underlying data store.</span></span> <span data-ttu-id="b2d80-105">Sem uma camada de abstração, os serviços de entidade podiam ser direcionados em um armazenamento de dados ou em um provedor de dados específico.</span><span class="sxs-lookup"><span data-stu-id="b2d80-105">Without a layer of abstraction, Entity Services could only be targeted at a specific data store or data provider.</span></span>  
  
 <span data-ttu-id="b2d80-106">Tipos que suporta do provedor são suportados direta ou indiretamente por base de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="b2d80-106">Types that the provider supports are directly or indirectly supported by the underlying database.</span></span> <span data-ttu-id="b2d80-107">Esses tipos não são necessariamente os tipos exatos de armazenamento, mas os tipos que o provedor usa para oferecer suporte [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b2d80-107">These types are not necessarily the exact store types, but the types the provider uses to support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="b2d80-108">Os tipos de provedor/armazenamento são descritos em termos de Modelo de Dados de Entidade (EDM).</span><span class="sxs-lookup"><span data-stu-id="b2d80-108">Provider/store types are described in the Entity Data Model (EDM) terms.</span></span>  
  
 <span data-ttu-id="b2d80-109">O parâmetro e tipos de retorno para as funções suportados pelo armazenamento de dados são especificados em termos de EDM.</span><span class="sxs-lookup"><span data-stu-id="b2d80-109">Parameter and return types for the functions supported by the data store are specified in EDM terms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2d80-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2d80-110">Requirements</span></span>  
 <span data-ttu-id="b2d80-111">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] e a necessidade de armazenamento de dados pode passar para frente e para trás dados em tipos conhecidos sem qualquer perda de dados ou truncamento.</span><span class="sxs-lookup"><span data-stu-id="b2d80-111">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and the data store need to be able to pass data back and forth in known types without any data loss or truncation.</span></span>  
  
 <span data-ttu-id="b2d80-112">O manifesto do provedor deve ser loadable por ferramentas em tempo de design sem ter que abrir uma conexão para o armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="b2d80-112">The provider manifest must be loadable by tools at design time without having to open a connection to the data store.</span></span>  
  
 <span data-ttu-id="b2d80-113">O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] é o caso confidenciais, mas o armazenamento de dados subjacente pode não ser.</span><span class="sxs-lookup"><span data-stu-id="b2d80-113">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is case sensitive, but the underlying data store may not be.</span></span> <span data-ttu-id="b2d80-114">Quando os artefatos de EDM (identificadores e nomes de tipo, por exemplo) são definidos e usados no manifesto, devem usar a maiúsculas de minúsculas [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b2d80-114">When EDM artifacts (identifiers and type names, for example) are defined and used in the manifest, they must use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] case sensitivity.</span></span> <span data-ttu-id="b2d80-115">Se os elementos do armazenamento de dados que podem ser maiúsculas de minúsculas aparecem no manifesto do provedor, essa caixa precisa ser mantidas no manifesto do provedor.</span><span class="sxs-lookup"><span data-stu-id="b2d80-115">If data store elements that may be case sensitive appear in the provider manifest, that casing needs to be maintained in the provider manifest.</span></span>  
  
 <span data-ttu-id="b2d80-116">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] requer um manifesto de provedor para todos os provedores de dados.</span><span class="sxs-lookup"><span data-stu-id="b2d80-116">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] requires a provider manifest for all data providers.</span></span> <span data-ttu-id="b2d80-117">Se você tentar usar um provedor que não tem um provedor de manifesto com o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], você obterá um erro.</span><span class="sxs-lookup"><span data-stu-id="b2d80-117">If you try to use a provider that does not have a provider manifest with the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you will get an error.</span></span>  
  
 <span data-ttu-id="b2d80-118">A tabela a seguir descreve os tipos de exceções que [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] jogaria quando ocorrerem exceções com a interação de provedor:</span><span class="sxs-lookup"><span data-stu-id="b2d80-118">The following table describes the kinds of exceptions the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] would throw when exceptions arise through provider interaction:</span></span>  
  
|<span data-ttu-id="b2d80-119">Problema</span><span class="sxs-lookup"><span data-stu-id="b2d80-119">Issue</span></span>|<span data-ttu-id="b2d80-120">Exceção</span><span class="sxs-lookup"><span data-stu-id="b2d80-120">Exception</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="b2d80-121">O provedor não oferece suporte GetProviderManifest em DbProviderServices.</span><span class="sxs-lookup"><span data-stu-id="b2d80-121">The Provider does not support GetProviderManifest in DbProviderServices.</span></span>|<span data-ttu-id="b2d80-122">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="b2d80-122">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="b2d80-123">Manifesto ausente do provedor: o provedor retorna `null` ao tentar recuperar o provedor de manifesto.</span><span class="sxs-lookup"><span data-stu-id="b2d80-123">Missing provider manifest: the provider returns `null` when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="b2d80-124">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="b2d80-124">ProviderIncompatibleException</span></span>|  
|<span data-ttu-id="b2d80-125">Manifesto inválido do provedor: o provedor retorna XML válido para tentar recuperar o provedor de manifesto.</span><span class="sxs-lookup"><span data-stu-id="b2d80-125">Invalid provider manifest: the provider returns invalid XML when attempting to retrieve the provider manifest.</span></span>|<span data-ttu-id="b2d80-126">ProviderIncompatibleException</span><span class="sxs-lookup"><span data-stu-id="b2d80-126">ProviderIncompatibleException</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="b2d80-127">Cenários</span><span class="sxs-lookup"><span data-stu-id="b2d80-127">Scenarios</span></span>  
 <span data-ttu-id="b2d80-128">Um provedor deve oferecer suporte aos seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="b2d80-128">A provider should support the following scenarios:</span></span>  
  
### <a name="writing-a-provider-with-symmetric-type-mapping"></a><span data-ttu-id="b2d80-129">Escrevendo um provedor com mapeamento simétrico de tipo</span><span class="sxs-lookup"><span data-stu-id="b2d80-129">Writing a Provider with Symmetric Type Mapping</span></span>  
 <span data-ttu-id="b2d80-130">Você pode escrever um provedor para o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] onde cada tipo de armazenamento é mapeado para um único tipo EDM, independentemente da direção de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="b2d80-130">You can write a provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] where each store type maps to a single EDM type, regardless of the mapping direction.</span></span> <span data-ttu-id="b2d80-131">Para um tipo de provedor que tenha o mapeamento muito simples que corresponde com um tipo de EDM, você pode usar uma solução simétrica porque o sistema de tipos é simples ou corresponde tipos de EDM.</span><span class="sxs-lookup"><span data-stu-id="b2d80-131">For a provider type that has very simple mapping that corresponds with an EDM type, you can use a symmetric solution because the type system is simple or matches EDM types.</span></span>  
  
 <span data-ttu-id="b2d80-132">Você pode usar a simplicidade do domínio e gerar um manifesto declarativo estática do provedor.</span><span class="sxs-lookup"><span data-stu-id="b2d80-132">You can use the simplicity of their domain and produce a static declarative provider manifest.</span></span>  
  
 <span data-ttu-id="b2d80-133">Você escreve um arquivo XML que tem duas seções:</span><span class="sxs-lookup"><span data-stu-id="b2d80-133">You write an XML file that has two sections:</span></span>  
  
-   <span data-ttu-id="b2d80-134">Uma lista de tipos de provedor expressos em termos de “de EDM contrapartes” de um tipo ou uma função de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="b2d80-134">A list of provider types expressed in terms of the "EDM counterpart" of a store type or function.</span></span> <span data-ttu-id="b2d80-135">Os tipos de Store têm tipos de EDM de correspondentes.</span><span class="sxs-lookup"><span data-stu-id="b2d80-135">Store types have counterpart EDM types.</span></span> <span data-ttu-id="b2d80-136">Funções de Store têm correspondentes funções de EDM.</span><span class="sxs-lookup"><span data-stu-id="b2d80-136">Store functions have corresponding EDM functions.</span></span> <span data-ttu-id="b2d80-137">Por exemplo, varchar é um tipo SQL Server mas o tipo correspondente de EDM é cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b2d80-137">For example, varchar is a SQL Server type but the corresponding EDM type is string.</span></span>  
  
-   <span data-ttu-id="b2d80-138">Uma lista de funções suportadas pelo provedor onde o parâmetro e tipos de retorno são expressos em termos de EDM.</span><span class="sxs-lookup"><span data-stu-id="b2d80-138">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
### <a name="writing-a-provider-with-asymmetric-type-mapping"></a><span data-ttu-id="b2d80-139">Escrevendo um provedor com mapeamento assimétrico de tipo</span><span class="sxs-lookup"><span data-stu-id="b2d80-139">Writing a Provider with Asymmetric Type Mapping</span></span>  
 <span data-ttu-id="b2d80-140">Ao escrever um provedor de armazenamento de dados para [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], o mapeamento de tipo de EDM-à- provedor para qualquer tipo pode ser diferente de mapeamento de tipo de provedor-à- EDM.</span><span class="sxs-lookup"><span data-stu-id="b2d80-140">When writing a data store provider for the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], the EDM-to-provider type mapping for some types may be different from provider-to-EDM type mapping.</span></span> <span data-ttu-id="b2d80-141">Por exemplo, EDM ilimitado PrimitiveTypeKind.String pode mapear a nvarchar (4000) no provedor, quando (4000) mapas nvarchar a EDM PrimitiveTypeKind.String (MaxLength=4000).</span><span class="sxs-lookup"><span data-stu-id="b2d80-141">For instance, unbounded EDM PrimitiveTypeKind.String may map to nvarchar(4000) on the provider, while nvarchar(4000) maps to the EDM PrimitiveTypeKind.String(MaxLength=4000).</span></span>  
  
 <span data-ttu-id="b2d80-142">Você escreve um arquivo XML que tem duas seções:</span><span class="sxs-lookup"><span data-stu-id="b2d80-142">You write an XML file that has two sections:</span></span>  
  
-   <span data-ttu-id="b2d80-143">Uma lista de tipos de provedor expressos em termos de EDM e define o mapeamento para ambos direção: EDM-à-provedor e provedor-à-EDM.</span><span class="sxs-lookup"><span data-stu-id="b2d80-143">A list of provider types expressed in EDM terms and define mapping for both direction: EDM-to-provider and provider-to-EDM.</span></span>  
  
-   <span data-ttu-id="b2d80-144">Uma lista de funções suportadas pelo provedor onde o parâmetro e tipos de retorno são expressos em termos de EDM.</span><span class="sxs-lookup"><span data-stu-id="b2d80-144">A list of functions supported by the provider where parameter and return types are expressed in EDM terms.</span></span>  
  
## <a name="provider-manifest-discoverability"></a><span data-ttu-id="b2d80-145">Descoberta manifesto provedor</span><span class="sxs-lookup"><span data-stu-id="b2d80-145">Provider Manifest Discoverability</span></span>  
 <span data-ttu-id="b2d80-146">O manifesto é usado por vários serviços indiretamente componentes de entidade dos tipos (por exemplo ferramentas ou consulta) mas aproveitado mais diretamente por metadados com o uso do carregador de metadados do armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="b2d80-146">The manifest is used indirectly by several component types in Entity Services (for example Tools or Query) but more directly leveraged by metadata through the use of the data store metadata loader.</span></span>  
  
 <span data-ttu-id="b2d80-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span><span class="sxs-lookup"><span data-stu-id="b2d80-147">![dfb3d02b&#45;7a8c&#45;4d51&#45;ac5a&#45;a73d8aa145e6](../../../../../docs/framework/data/adonet/ef/media/dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6.gif "dfb3d02b-7a8c-4d51-ac5a-a73d8aa145e6")</span></span>  
  
 <span data-ttu-id="b2d80-148">No entanto, um provedor determinado pode suportar armazenamentos diferentes ou versões diferentes do mesmo armazenamento.</span><span class="sxs-lookup"><span data-stu-id="b2d80-148">However, a given provider may support different stores or different versions of the same store.</span></span> <span data-ttu-id="b2d80-149">Portanto, um provedor deve relatar um manifesto diferente para cada armazenamento de dados suportado.</span><span class="sxs-lookup"><span data-stu-id="b2d80-149">Therefore, a provider must report a different manifest for each supported data store.</span></span>  
  
### <a name="provider-manifest-token"></a><span data-ttu-id="b2d80-150">Símbolo manifesto do provedor</span><span class="sxs-lookup"><span data-stu-id="b2d80-150">Provider Manifest Token</span></span>  
 <span data-ttu-id="b2d80-151">Quando uma conexão de armazenamento de dados é aberta, o provedor pode consultar informações que retorna o manifesto direito.</span><span class="sxs-lookup"><span data-stu-id="b2d80-151">When a data store connection is opened, the provider can query for information to return the right manifest.</span></span> <span data-ttu-id="b2d80-152">Isso pode não ser possível em situações onde off-line informações de conexão não está disponível ou quando não é possível conectar-se ao armazenamento.</span><span class="sxs-lookup"><span data-stu-id="b2d80-152">This may not be possible in offline scenarios where connection information is not available or when it is not possible to connect to the store.</span></span> <span data-ttu-id="b2d80-153">Identifica o manifesto usando o atributo `ProviderManifestToken` do elemento de `Schema` no arquivo de .ssdl.</span><span class="sxs-lookup"><span data-stu-id="b2d80-153">Identify the manifest by using the `ProviderManifestToken` attribute of the `Schema` element in the .ssdl file.</span></span> <span data-ttu-id="b2d80-154">Não há nenhum formato exigido para este atributo; o provedor escolher informações mínima necessária identificar um manifesto sem abrir uma conexão para o armazenamento.</span><span class="sxs-lookup"><span data-stu-id="b2d80-154">There is no required format for this attribute; the provider chooses the minimum information needed to identify a manifest without opening a connection to the store.</span></span>  
  
 <span data-ttu-id="b2d80-155">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b2d80-155">For example:</span></span>  
  
```xml  
<Schema Namespace="Northwind" Provider="System.Data.SqlClient" ProviderManifestToken="2005" xmlns:edm="http://schemas.microsoft.com/ado/2006/04/edm/ssdl" xmlns="http://schemas.microsoft.com/ado/2006/04/edm/ssdl">  
```  
  
## <a name="provider-manifest-programming-model"></a><span data-ttu-id="b2d80-156">Manifesto modelo de programação do provedor</span><span class="sxs-lookup"><span data-stu-id="b2d80-156">Provider Manifest Programming Model</span></span>  
 <span data-ttu-id="b2d80-157">Os provedores derivam de <xref:System.Data.Common.DbXmlEnabledProviderManifest>, que permite que especifiquem seus manifestos declarativamente.</span><span class="sxs-lookup"><span data-stu-id="b2d80-157">Providers derive from <xref:System.Data.Common.DbXmlEnabledProviderManifest>, which allows them to specify their manifests declaratively.</span></span> <span data-ttu-id="b2d80-158">A ilustração a seguir mostra a hierarquia de classe de um provedor:</span><span class="sxs-lookup"><span data-stu-id="b2d80-158">The following illustration shows the class hierarchy of a provider:</span></span>  
  
 <span data-ttu-id="b2d80-159">![None](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span><span class="sxs-lookup"><span data-stu-id="b2d80-159">![None](../../../../../docs/framework/data/adonet/ef/media/d541eba3-2ee6-4cd1-88f5-89d0b2582a6c.gif "d541eba3-2ee6-4cd1-88f5-89d0b2582a6c")</span></span>  
  
### <a name="discoverability-api"></a><span data-ttu-id="b2d80-160">Descoberta API</span><span class="sxs-lookup"><span data-stu-id="b2d80-160">Discoverability API</span></span>  
 <span data-ttu-id="b2d80-161">O manifesto do provedor é carregado pelo carregador de metadados de Store (StoreItemCollection), usando uma conexão de armazenamento de dados ou um token de manifesto do provedor.</span><span class="sxs-lookup"><span data-stu-id="b2d80-161">The provider manifest is loaded by the Store Metadata loader (StoreItemCollection), either by using a data store connection or a provider manifest token.</span></span>  
  
#### <a name="using-a-data-store-connection"></a><span data-ttu-id="b2d80-162">Usando uma conexão do armazenamento de dados</span><span class="sxs-lookup"><span data-stu-id="b2d80-162">Using a Data Store Connection</span></span>  
 <span data-ttu-id="b2d80-163">Quando a conexão do armazenamento de dados está disponível, a chamada DbProvderServices.GetProviderManifestToken para retornar o símbolo que é passado para o método de GetProviderManifest, que retorna DbProviderManifest.</span><span class="sxs-lookup"><span data-stu-id="b2d80-163">When the data store connection is available, call DbProvderServices.GetProviderManifestToken to return the token that is passed to the GetProviderManifest method, which returns DbProviderManifest.</span></span> <span data-ttu-id="b2d80-164">Representantes desse método para a implementação de provedor de GetDbProviderManifestToken.</span><span class="sxs-lookup"><span data-stu-id="b2d80-164">This method delegates to the provider's implementation of GetDbProviderManifestToken.</span></span>  
  
```  
public string GetProviderManifestToken(DbConnection connection);  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
#### <a name="using-a-provider-manifest-token"></a><span data-ttu-id="b2d80-165">Usando um token de manifesto de provedor</span><span class="sxs-lookup"><span data-stu-id="b2d80-165">Using a Provider Manifest Token</span></span>  
 <span data-ttu-id="b2d80-166">Para o cenário off-line, o símbolo é escolhido da representação de SSDL.</span><span class="sxs-lookup"><span data-stu-id="b2d80-166">For the offline scenario, the token is picked from SSDL representation.</span></span> <span data-ttu-id="b2d80-167">SSDL permite que você especifique um ProviderManifestToken (consulte [o elemento de esquema (SSDL)](https://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222) para obter mais informações).</span><span class="sxs-lookup"><span data-stu-id="b2d80-167">The SSDL allows you to specify a ProviderManifestToken (see [Schema Element (SSDL)](https://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222) for more information).</span></span> <span data-ttu-id="b2d80-168">Por exemplo, se uma conexão não pode ser aberta, SSDL tem um token de manifesto de provedor que especifica informações sobre o manifesto.</span><span class="sxs-lookup"><span data-stu-id="b2d80-168">For example, if a connection cannot be opened, the SSDL has a provider manifest token that specifies information about the manifest.</span></span>  
  
```  
public DbProviderManifest GetProviderManifest(string manifestToken);  
```  
  
### <a name="provider-manifest-schema"></a><span data-ttu-id="b2d80-169">Esquema manifesto do provedor</span><span class="sxs-lookup"><span data-stu-id="b2d80-169">Provider Manifest Schema</span></span>  
 <span data-ttu-id="b2d80-170">O esquema de informações definido para cada provedor contém informações estáticas a ser consumida por metadados:</span><span class="sxs-lookup"><span data-stu-id="b2d80-170">The schema of information defined for each provider contains the static information to be consumed by metadata:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema elementFormDefault="qualified"  
   xmlns:xs="http://www.w3.org/2001/XMLSchema"  
   targetNamespace="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest"  
   xmlns:pm="http://schemas.microsoft.com/ado/2006/04/edm/providermanifest">  
  
  <xs:element name="ProviderManifest">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Types" type="pm:TTypes" minOccurs="1" maxOccurs="1" />  
        <xs:element name="Functions" type="pm:TFunctions" minOccurs="0" maxOccurs="1"/>  
      </xs:sequence>  
      <xs:attribute name="Namespace" type="xs:string" use="required"/>  
    </xs:complexType>  
  </xs:element>  
  <xs:complexType name="TVersion">  
    <xs:attribute name="Major" type="xs:int" use="required" />  
    <xs:attribute name="Minor" type="xs:int" use="required" />  
    <xs:attribute name="Build" type="xs:int" use="required" />  
    <xs:attribute name="Revision" type="xs:int" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TIntegerFacetDescription">  
    <xs:attribute name="Minimum" type="xs:int" use="optional" />  
    <xs:attribute name="Maximum" type="xs:int" use="optional" />  
    <xs:attribute name="DefaultValue" type="xs:int" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TBooleanFacetDescription">  
    <xs:attribute name="DefaultValue" type="xs:boolean" use="optional" />  
    <xs:attribute name="Constant" type="xs:boolean" default="true" />  
  </xs:complexType>  
  
  <xs:complexType name="TDateTimeFacetDescription">  
    <xs:attribute name="Constant" type="xs:boolean" default="false" />  
  </xs:complexType>  
  
  <xs:complexType name="TFacetDescriptions">  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="Precision" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Scale" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="MaxLength" minOccurs="0" maxOccurs="1" type="pm:TIntegerFacetDescription"/>  
      <xs:element name="Unicode" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
      <xs:element name="FixedLength" minOccurs="0" maxOccurs="1" type="pm:TBooleanFacetDescription"/>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:complexType name="TType">  
    <xs:sequence>  
      <xs:element name="FacetDescriptions" type="pm:TFacetDescriptions" minOccurs="0" maxOccurs="1"/>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required"/>  
    <xs:attribute name="PrimitiveTypeKind" type="pm:TPrimitiveTypeKind" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TTypes">  
    <xs:sequence>  
      <xs:element name="Type" type="pm:TType" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:attributeGroup name="TFacetAttribute">  
    <xs:attribute name="Precision" type="xs:int" use="optional"/>  
    <xs:attribute name="Scale" type="xs:int" use="optional"/>  
    <xs:attribute name="MaxLength" type="xs:int" use="optional"/>  
    <xs:attribute name="Unicode" type="xs:boolean" use="optional"/>  
    <xs:attribute name="FixedLength" type="xs:boolean" use="optional"/>  
  </xs:attributeGroup>  
  
  <xs:complexType name="TFunctionParameter">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
    <xs:attribute name="Mode" type="pm:TParameterDirection" use="required" />  
  </xs:complexType>  
  
  <xs:complexType name="TReturnType">  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attributeGroup ref="pm:TFacetAttribute" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunction">  
    <xs:choice minOccurs="0" maxOccurs ="unbounded">  
      <xs:element name ="ReturnType" type="pm:TReturnType" minOccurs="0" maxOccurs="1" />  
      <xs:element name="Parameter" type="pm:TFunctionParameter" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:choice>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Aggregate" type="xs:boolean" use="optional" />  
    <xs:attribute name="BuiltIn" type="xs:boolean" use="optional" />  
    <xs:attribute name="StoreFunctionName" type="xs:string" use="optional" />  
    <xs:attribute name="NiladicFunction" type="xs:boolean" use="optional" />  
    <xs:attribute name="ParameterTypeSemantics" type="pm:TParameterTypeSemantics" use="optional" default="AllowImplicitConversion" />  
  </xs:complexType>  
  
  <xs:complexType name="TFunctions">  
    <xs:sequence>  
      <xs:element name="Function" type="pm:TFunction" minOccurs="0" maxOccurs="unbounded"/>  
    </xs:sequence>  
  </xs:complexType>  
  
  <xs:simpleType name="TPrimitiveTypeKind">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Binary"/>  
      <xs:enumeration value="Boolean"/>  
      <xs:enumeration value="Byte"/>  
      <xs:enumeration value="Decimal"/>  
      <xs:enumeration value="DateTime"/>  
      <xs:enumeration value="Time"/>  
      <xs:enumeration value="DateTimeOffset"/>          
      <xs:enumeration value="Double"/>  
      <xs:enumeration value="Guid"/>  
      <xs:enumeration value="Single"/>  
      <xs:enumeration value="SByte"/>  
      <xs:enumeration value="Int16"/>  
      <xs:enumeration value="Int32"/>  
      <xs:enumeration value="Int64"/>  
      <xs:enumeration value="String"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In"/>  
      <xs:enumeration value="Out"/>  
      <xs:enumeration value="InOut"/>  
    </xs:restriction>  
  </xs:simpleType>  
  
  <xs:simpleType name="TParameterTypeSemantics">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="ExactMatchOnly" />  
      <xs:enumeration value="AllowImplicitPromotion" />  
      <xs:enumeration value="AllowImplicitConversion" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
#### <a name="types-node"></a><span data-ttu-id="b2d80-171">Nó de tipos</span><span class="sxs-lookup"><span data-stu-id="b2d80-171">Types Node</span></span>  
 <span data-ttu-id="b2d80-172">O nó de tipos no manifesto do provedor contém informações sobre os tipos que são suportados originalmente pelo armazenamento de dados ou do provedor.</span><span class="sxs-lookup"><span data-stu-id="b2d80-172">The Types node in the provider manifest contains information about the Types that are supported natively by the data store or through the provider.</span></span>  
  
##### <a name="type-node"></a><span data-ttu-id="b2d80-173">Nó de tipo</span><span class="sxs-lookup"><span data-stu-id="b2d80-173">Type Node</span></span>  
 <span data-ttu-id="b2d80-174">Cada nó do tipo define um tipo de provedor em termos de EDM.</span><span class="sxs-lookup"><span data-stu-id="b2d80-174">Each Type node defines a provider type in terms of EDM.</span></span> <span data-ttu-id="b2d80-175">O nó do tipo descrevem o nome do tipo do provedor, e informações acrescentadas ao tipo que mapeia o modelo e facetas para descrever o mapeamento de tipo.</span><span class="sxs-lookup"><span data-stu-id="b2d80-175">The Type node describes the name of the provider type, and information related to the model type it maps to and facets to describe that type mapping.</span></span>  
  
 <span data-ttu-id="b2d80-176">Para expressar essas informações de tipo no manifesto do provedor, cada declaração de TypeInformation deve definir várias descrições de aspecto para cada tipo:</span><span class="sxs-lookup"><span data-stu-id="b2d80-176">In order to express this type information in the provider manifest, each TypeInformation declaration must define several facet descriptions for each Type:</span></span>  
  
|<span data-ttu-id="b2d80-177">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="b2d80-177">Attribute Name</span></span>|<span data-ttu-id="b2d80-178">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="b2d80-178">Data Type</span></span>|<span data-ttu-id="b2d80-179">Necessária</span><span class="sxs-lookup"><span data-stu-id="b2d80-179">Required</span></span>|<span data-ttu-id="b2d80-180">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="b2d80-180">Default Value</span></span>|<span data-ttu-id="b2d80-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2d80-181">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="b2d80-182">Nome</span><span class="sxs-lookup"><span data-stu-id="b2d80-182">Name</span></span>|<span data-ttu-id="b2d80-183">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b2d80-183">String</span></span>|<span data-ttu-id="b2d80-184">Sim</span><span class="sxs-lookup"><span data-stu-id="b2d80-184">Yes</span></span>|<span data-ttu-id="b2d80-185">N/D</span><span class="sxs-lookup"><span data-stu-id="b2d80-185">n/a</span></span>|<span data-ttu-id="b2d80-186">Nome do provedor específico de tipo de dados</span><span class="sxs-lookup"><span data-stu-id="b2d80-186">Provider-specific data type name</span></span>|  
|<span data-ttu-id="b2d80-187">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="b2d80-187">PrimitiveTypeKind</span></span>|<span data-ttu-id="b2d80-188">PrimitiveTypeKind</span><span class="sxs-lookup"><span data-stu-id="b2d80-188">PrimitiveTypeKind</span></span>|<span data-ttu-id="b2d80-189">Sim</span><span class="sxs-lookup"><span data-stu-id="b2d80-189">Yes</span></span>|<span data-ttu-id="b2d80-190">N/D</span><span class="sxs-lookup"><span data-stu-id="b2d80-190">n/a</span></span>|<span data-ttu-id="b2d80-191">Nome do tipo de EDM</span><span class="sxs-lookup"><span data-stu-id="b2d80-191">EDM type name</span></span>|  
  
###### <a name="function-node"></a><span data-ttu-id="b2d80-192">Nó de função</span><span class="sxs-lookup"><span data-stu-id="b2d80-192">Function Node</span></span>  
 <span data-ttu-id="b2d80-193">Cada função define uma única função disponível através do provedor.</span><span class="sxs-lookup"><span data-stu-id="b2d80-193">Each Function defines a single function available through the provider.</span></span>  
  
|<span data-ttu-id="b2d80-194">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="b2d80-194">Attribute Name</span></span>|<span data-ttu-id="b2d80-195">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="b2d80-195">Data Type</span></span>|<span data-ttu-id="b2d80-196">Necessária</span><span class="sxs-lookup"><span data-stu-id="b2d80-196">Required</span></span>|<span data-ttu-id="b2d80-197">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="b2d80-197">Default Value</span></span>|<span data-ttu-id="b2d80-198">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2d80-198">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="b2d80-199">Nome</span><span class="sxs-lookup"><span data-stu-id="b2d80-199">Name</span></span>|<span data-ttu-id="b2d80-200">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b2d80-200">String</span></span>|<span data-ttu-id="b2d80-201">Sim</span><span class="sxs-lookup"><span data-stu-id="b2d80-201">Yes</span></span>|<span data-ttu-id="b2d80-202">N/D</span><span class="sxs-lookup"><span data-stu-id="b2d80-202">n/a</span></span>|<span data-ttu-id="b2d80-203">Identificador/nome de função</span><span class="sxs-lookup"><span data-stu-id="b2d80-203">Identifier/name of the function</span></span>|  
|<span data-ttu-id="b2d80-204">Tipoderetorno</span><span class="sxs-lookup"><span data-stu-id="b2d80-204">ReturnType</span></span>|<span data-ttu-id="b2d80-205">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="b2d80-205">String</span></span>|<span data-ttu-id="b2d80-206">Não</span><span class="sxs-lookup"><span data-stu-id="b2d80-206">No</span></span>|<span data-ttu-id="b2d80-207">Void</span><span class="sxs-lookup"><span data-stu-id="b2d80-207">Void</span></span>|<span data-ttu-id="b2d80-208">O tipo de retorno de EDM de função</span><span class="sxs-lookup"><span data-stu-id="b2d80-208">The EDM return type of the function</span></span>|  
|<span data-ttu-id="b2d80-209">Agregado</span><span class="sxs-lookup"><span data-stu-id="b2d80-209">Aggregate</span></span>|<span data-ttu-id="b2d80-210">Boolean</span><span class="sxs-lookup"><span data-stu-id="b2d80-210">Boolean</span></span>|<span data-ttu-id="b2d80-211">Não</span><span class="sxs-lookup"><span data-stu-id="b2d80-211">No</span></span>|<span data-ttu-id="b2d80-212">False</span><span class="sxs-lookup"><span data-stu-id="b2d80-212">False</span></span>|<span data-ttu-id="b2d80-213">Retifique se a função é uma função agregada</span><span class="sxs-lookup"><span data-stu-id="b2d80-213">True if the function is an aggregate function</span></span>|  
|<span data-ttu-id="b2d80-214">Internos</span><span class="sxs-lookup"><span data-stu-id="b2d80-214">BuiltIn</span></span>|<span data-ttu-id="b2d80-215">Boolean</span><span class="sxs-lookup"><span data-stu-id="b2d80-215">Boolean</span></span>|<span data-ttu-id="b2d80-216">Não</span><span class="sxs-lookup"><span data-stu-id="b2d80-216">No</span></span>|<span data-ttu-id="b2d80-217">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="b2d80-217">True</span></span>|<span data-ttu-id="b2d80-218">Retifique se a função é compilada no armazenamento de dados</span><span class="sxs-lookup"><span data-stu-id="b2d80-218">True if the function is built into the data store</span></span>|  
|<span data-ttu-id="b2d80-219">StoreFunctionName</span><span class="sxs-lookup"><span data-stu-id="b2d80-219">StoreFunctionName</span></span>|<span data-ttu-id="b2d80-220">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="b2d80-220">String</span></span>|<span data-ttu-id="b2d80-221">Não</span><span class="sxs-lookup"><span data-stu-id="b2d80-221">No</span></span>|<span data-ttu-id="b2d80-222">\<Nome ></span><span class="sxs-lookup"><span data-stu-id="b2d80-222">\<Name></span></span>|<span data-ttu-id="b2d80-223">Nome de função no armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="b2d80-223">Function Name in the data store.</span></span>  <span data-ttu-id="b2d80-224">Permite um nível de redirecionamento de nomes de função.</span><span class="sxs-lookup"><span data-stu-id="b2d80-224">Allows for a level of redirection of function names.</span></span>|  
|<span data-ttu-id="b2d80-225">NiladicFunction</span><span class="sxs-lookup"><span data-stu-id="b2d80-225">NiladicFunction</span></span>|<span data-ttu-id="b2d80-226">Boolean</span><span class="sxs-lookup"><span data-stu-id="b2d80-226">Boolean</span></span>|<span data-ttu-id="b2d80-227">Não</span><span class="sxs-lookup"><span data-stu-id="b2d80-227">No</span></span>|<span data-ttu-id="b2d80-228">False</span><span class="sxs-lookup"><span data-stu-id="b2d80-228">False</span></span>|<span data-ttu-id="b2d80-229">Retifique se a função não requer parâmetros e é chamado sem nenhum parâmetro</span><span class="sxs-lookup"><span data-stu-id="b2d80-229">True if the function does not require parameters and is called without any parameters</span></span>|  
|<span data-ttu-id="b2d80-230">ParameterType</span><span class="sxs-lookup"><span data-stu-id="b2d80-230">ParameterType</span></span><br /><br /> <span data-ttu-id="b2d80-231">Semântica</span><span class="sxs-lookup"><span data-stu-id="b2d80-231">Semantics</span></span>|<span data-ttu-id="b2d80-232">ParameterSemantics</span><span class="sxs-lookup"><span data-stu-id="b2d80-232">ParameterSemantics</span></span>|<span data-ttu-id="b2d80-233">Não</span><span class="sxs-lookup"><span data-stu-id="b2d80-233">No</span></span>|<span data-ttu-id="b2d80-234">AllowImplicit</span><span class="sxs-lookup"><span data-stu-id="b2d80-234">AllowImplicit</span></span><br /><br /> <span data-ttu-id="b2d80-235">Conversão</span><span class="sxs-lookup"><span data-stu-id="b2d80-235">Conversion</span></span>|<span data-ttu-id="b2d80-236">Escolha de como o pipeline de consulta deve manipular a substituição do tipo de parâmetro:</span><span class="sxs-lookup"><span data-stu-id="b2d80-236">Choice of how the query pipeline should deal with parameter type substitution:</span></span><br /><br /> <span data-ttu-id="b2d80-237">-ExactMatchOnly</span><span class="sxs-lookup"><span data-stu-id="b2d80-237">-   ExactMatchOnly</span></span><br /><span data-ttu-id="b2d80-238">-AllowImplicitPromotion</span><span class="sxs-lookup"><span data-stu-id="b2d80-238">-   AllowImplicitPromotion</span></span><br /><span data-ttu-id="b2d80-239">-AllowImplicitConversion</span><span class="sxs-lookup"><span data-stu-id="b2d80-239">-   AllowImplicitConversion</span></span>|  
  
 <span data-ttu-id="b2d80-240">**Nó de parâmetros**</span><span class="sxs-lookup"><span data-stu-id="b2d80-240">**Parameters Node**</span></span>  
  
 <span data-ttu-id="b2d80-241">Cada função tem uma coleção de um ou mais nós de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b2d80-241">Each function has a collection of one or more Parameter nodes.</span></span>  
  
|<span data-ttu-id="b2d80-242">Nome do atributo</span><span class="sxs-lookup"><span data-stu-id="b2d80-242">Attribute Name</span></span>|<span data-ttu-id="b2d80-243">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="b2d80-243">Data Type</span></span>|<span data-ttu-id="b2d80-244">Necessária</span><span class="sxs-lookup"><span data-stu-id="b2d80-244">Required</span></span>|<span data-ttu-id="b2d80-245">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="b2d80-245">Default Value</span></span>|<span data-ttu-id="b2d80-246">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2d80-246">Description</span></span>|  
|--------------------|---------------|--------------|-------------------|-----------------|  
|<span data-ttu-id="b2d80-247">Nome</span><span class="sxs-lookup"><span data-stu-id="b2d80-247">Name</span></span>|<span data-ttu-id="b2d80-248">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b2d80-248">String</span></span>|<span data-ttu-id="b2d80-249">Sim</span><span class="sxs-lookup"><span data-stu-id="b2d80-249">Yes</span></span>|<span data-ttu-id="b2d80-250">N/D</span><span class="sxs-lookup"><span data-stu-id="b2d80-250">n/a</span></span>|<span data-ttu-id="b2d80-251">Identificador/nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b2d80-251">Identifier/name of the parameter.</span></span>|  
|<span data-ttu-id="b2d80-252">Tipo</span><span class="sxs-lookup"><span data-stu-id="b2d80-252">Type</span></span>|<span data-ttu-id="b2d80-253">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="b2d80-253">String</span></span>|<span data-ttu-id="b2d80-254">Sim</span><span class="sxs-lookup"><span data-stu-id="b2d80-254">Yes</span></span>|<span data-ttu-id="b2d80-255">N/D</span><span class="sxs-lookup"><span data-stu-id="b2d80-255">n/a</span></span>|<span data-ttu-id="b2d80-256">O tipo de EDM de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b2d80-256">The EDM type of the parameter.</span></span>|  
|<span data-ttu-id="b2d80-257">Modo</span><span class="sxs-lookup"><span data-stu-id="b2d80-257">Mode</span></span>|<span data-ttu-id="b2d80-258">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="b2d80-258">Parameter</span></span><br /><br /> <span data-ttu-id="b2d80-259">Direção</span><span class="sxs-lookup"><span data-stu-id="b2d80-259">Direction</span></span>|<span data-ttu-id="b2d80-260">Sim</span><span class="sxs-lookup"><span data-stu-id="b2d80-260">Yes</span></span>|<span data-ttu-id="b2d80-261">N/D</span><span class="sxs-lookup"><span data-stu-id="b2d80-261">n/a</span></span>|<span data-ttu-id="b2d80-262">Direção do parâmetro:</span><span class="sxs-lookup"><span data-stu-id="b2d80-262">Direction of parameter:</span></span><br /><br /> <span data-ttu-id="b2d80-263">-no</span><span class="sxs-lookup"><span data-stu-id="b2d80-263">-   in</span></span><br /><span data-ttu-id="b2d80-264">-out</span><span class="sxs-lookup"><span data-stu-id="b2d80-264">-   out</span></span><br /><span data-ttu-id="b2d80-265">-inout</span><span class="sxs-lookup"><span data-stu-id="b2d80-265">-   inout</span></span>|  
  
##### <a name="namespace-attribute"></a><span data-ttu-id="b2d80-266">Atributo do namespace</span><span class="sxs-lookup"><span data-stu-id="b2d80-266">Namespace Attribute</span></span>  
 <span data-ttu-id="b2d80-267">Cada provedor de armazenamento de dados deve definir um namespace ou um grupo de namespaces para informações definida no manifesto.</span><span class="sxs-lookup"><span data-stu-id="b2d80-267">Each data store provider must define a namespace or group of namespaces for information defined in the manifest.</span></span> <span data-ttu-id="b2d80-268">Este namespace pode ser usada em consultas Entity SQL para resolver nomes das funções e tipos.</span><span class="sxs-lookup"><span data-stu-id="b2d80-268">This namespace can be used in Entity SQL queries to resolve names of functions and types.</span></span> <span data-ttu-id="b2d80-269">Por exemplo: SqlServer.</span><span class="sxs-lookup"><span data-stu-id="b2d80-269">For instance: SqlServer.</span></span> <span data-ttu-id="b2d80-270">O namespace deve ser diferente de namespace canônica, EDM, definido por serviços de entidade para que as funções padrão são suportadas por Entity consultas SQL.</span><span class="sxs-lookup"><span data-stu-id="b2d80-270">That namespace must be different from the canonical namespace, EDM, defined by Entity Services for standard functions to be supported by Entity SQL queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d80-271">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2d80-271">See Also</span></span>  
 [<span data-ttu-id="b2d80-272">Escrevendo um Provedor de Dados do Entity Framework</span><span class="sxs-lookup"><span data-stu-id="b2d80-272">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
