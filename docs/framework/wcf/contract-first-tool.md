---
title: Ferramenta Contract-First
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: b8d38cc31eacf1d8eb29aaaf7d6ef29056ff9b79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="contract-first-tool"></a>Ferramenta Contract-First
Contratos de serviço geralmente precisam ser criado a partir de serviços existentes. Em [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], classes de contrato de dados podem ser criadas automaticamente, de serviços existentes usando a ferramenta de contrato, primeiro. Para usar a ferramenta de contrato, primeiro, o arquivo de definição de esquema XML (XSD) deve ser baixado localmente; a ferramenta não é possível importar os contratos de dados remotos por meio de HTTP.  
  
 A ferramenta de contrato, primeiro é integrada ao [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] como uma tarefa de compilação. Os arquivos de código gerados pela tarefa de compilação são criados toda vez que o projeto é compilado, para que o projeto pode adotar facilmente as alterações no contrato de serviço subjacente.  
  
 Tipos de esquema que a ferramenta do primeiro contrato pode importar incluem o seguinte:  
  
```xml  
<xsd:complexType>  
<xsd:simpleType>  
```  
  
 Tipos simples não serão gerados se forem tipos primitivos como `Int16` ou `String`; complexos tipos não serão gerados se eles são do tipo `Collection`. Tipos também não serão gerados se fizerem parte de outro `xsd:complexType`. Nesses casos, os tipos serão referenciados para tipos existentes no projeto em vez disso.  
  
## <a name="adding-a-data-contract-to-a-project"></a>Adicionando um contrato de dados a um projeto  
 Antes da ferramenta do primeiro contrato pode ser usada, o contrato de serviço (XSD) deve ser adicionado ao projeto. Para os fins desta visão geral, o contrato a seguir será usado para ilustrar as funções de contrato, primeiro. Esta definição de serviço é um pequeno subconjunto de contrato de serviço usado pela API de pesquisa de Bing.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="ServiceSchema"  
    targetNamespace="http://tempuri.org/ServiceSchema.xsd"  
    elementFormDefault="qualified"  
    xmlns="http://tempuri.org/ServiceSchema.xsd"  
    xmlns:mstns="http://tempuri.org/ServiceSchema.xsd"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema"  
>  
  <xs:complexType name="SearchRequest">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="1" name="Version" type="xs:string" default="2.2" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Market" type="xs:string" />  
      <xs:element minOccurs="0" maxOccurs="1" name="UILanguage" type="xs:string" />  
      <xs:element minOccurs="1" maxOccurs="1" name="Query" type="xs:string" />  
      <xs:element minOccurs="1" maxOccurs="1" name="AppId" type="xs:string" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Latitude" type="xs:double" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Longitude" type="xs:double" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Radius" type="xs:double" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:simpleType name="WebSearchOption">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="DisableHostCollapsing" />  
      <xs:enumeration value="DisableQueryAlterations" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
 Para adicionar o contrato de serviço acima para o projeto, clique com o botão direito e selecione **adicionar novo...** . Selecione a definição de esquema do painel WCF da caixa de diálogo modelos e nomeie o novo arquivo SampleContract.xsd. Copie e cole o código acima para o modo de exibição de código do novo arquivo.  
  
## <a name="configuring-contract-first-options"></a>Configurando opções de primeiro contrato  
 Opções de contrato, primeiro podem ser configuradas no menu de propriedades de um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projeto. Para habilitar o desenvolvimento de contrato, primeiro, selecione o **habilitar XSD como linguagem de definição de tipo** caixa de seleção na página de WCF da janela de propriedades do projeto.  
  
 ![Mostrando opções de projeto do WCF contrato&#45;primeiro](../../../docs/framework/wcf/media/contractfirstoptions.png "ContractFirstOptions")  
  
 Para configurar propriedades avançadas, clique no botão Avançado.  
  
 ![Advanced contrato&#45;propriedades primeiro](../../../docs/framework/wcf/media/contractfirstadvanced.png "ContractFirstAdvanced")  
  
 As seguintes configurações avançadas podem ser configuradas para geração de código de contratos. As configurações só podem ser configuradas para todos os arquivos no projeto; as configurações não podem ser configuradas para arquivos individuais no momento.  
  
-   **Modo de serializador**: essa configuração determina qual serializador é usado para ler arquivos de contrato de serviço. Quando **serializador XML** for selecionada, o **tipos de coleção** e **reutilizar tipos** opções serão desabilitadas. Essas opções se aplicam somente para o **serializador de contrato de dados**.  
  
-   **Reutilizar tipos**: essa configuração especifica quais bibliotecas são usadas para reutilização de tipo. Essa configuração se aplica somente se **modo serializador** é definido como **serializador de contrato de dados**.  
  
-   **Tipo de coleção**: essa configuração especifica o tipo totalmente qualificado ou qualificado por assembly a ser usado para o tipo de dados da coleção. Essa configuração se aplica somente se **modo serializador** é definido como **serializador de contrato de dados**.  
  
-   **Tipo de dicionário**: essa configuração especifica o tipo totalmente qualificado ou qualificado por assembly a ser usado para o tipo de dados do dicionário.  
  
-   **EnableDataBinding**: essa configuração especifica se deve implementar o <xref:System.ComponentModel.INotifyPropertyChanged> interface em todos os tipos de dados para implementar a associação de dados.  
  
-   **ExcludedTypes**: essa configuração especifica a lista de tipos totalmente qualificado ou qualificado por assembly a serem excluídos os assemblies referenciados. Essa configuração se aplica somente se **modo serializador** é definido como **serializador de contrato de dados**.  
  
-   **GenerateInternalTypes**: essa configuração especifica se é para gerar classes que são marcados como internos. Essa configuração se aplica somente se **modo serializador** é definido como **serializador de contrato de dados**.  
  
-   **GenerateSerializableTypes**: essa configuração especifica se deve gerar classes com o <xref:System.SerializableAttribute> atributo. Essa configuração se aplica somente se **modo serializador** é definido como **serializador de contrato de dados**.  
  
-   **ImportXMLTypes**: essa configuração especifica se deve configurar o serializador de contrato de dados para aplicar o <xref:System.SerializableAttribute> atributo classes sem o <xref:System.Runtime.Serialization.DataContractAttribute> atributo.  Essa configuração se aplica somente se **modo serializador** é definido como **serializador de contrato de dados**.  
  
-   **SupportFx35TypedDataSets**: essa configuração especifica se fornecer funcionalidade adicional para conjuntos de dados tipados criados para o .net Framework 3.5. Quando **modo serializador** é definido como **serializador XML**, o <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> extensão será adicionada para o importador de esquema XML quando esse valor é definido como True. Quando **modo serializador** é definido como **serializador de contrato de dados**, o tipo <xref:System.DateTimeOffset> serão excluídos das referências quando esse valor é definido como False, para que um <xref:System.DateTimeOffset> sempre é gerada para versões mais antigas do framework.  
  
-   **InputXsdFiles**: essa configuração especifica a lista de arquivos de entrada. Cada arquivo deve conter um esquema XML válido.  
  
-   **Idioma**: essa configuração especifica o idioma de código de contrato gerado. A configuração deve ser reconhecida pelo <xref:System.CodeDom.Compiler.CodeDomProvider>.  
  
-   **NamespaceMappings**: essa configuração especifica os mapeamentos de Namespaces de destino de XSD para namespaces CLR. Cada mapeamento deve usar o seguinte formato:  
  
    ```xml  
    "<Schema Namespace>, <CLR Namespace>"  
    ```  
  
     O serializador XML aceita apenas um mapeamento no seguinte formato:  
  
    ```xml  
    "*, <CLR Namespace>"  
    ```  
  
-   **OutputDirectory**: essa configuração especifica o diretório onde os arquivos de código serão gerados.  
  
 As configurações serão usadas para gerar tipos de contrato de serviço dos arquivos de contrato de serviço quando o projeto é compilado.  
  
## <a name="using-contract-first-development"></a>Usando o desenvolvimento de primeiro contrato  
 Depois de adicionar o contrato de serviço para o projeto e confirmar as configurações de compilação, compilar o projeto, pressionando **F6**. Os tipos definidos no contrato de serviço, em seguida, estarão disponíveis para uso no projeto.  
  
 Para usar os tipos definidos no contrato de serviço, adicione uma referência a `ContractTypes` sob o namespace atual:  
  
```csharp  
using MyProjectNamespace.ContractTypes;  
```  
  
 Os tipos definidos no contrato de serviço será resolvidos no projeto, conforme mostrado abaixo.  
  
 ![Usando tipos derivados de um contrato de serviço](../../../docs/framework/wcf/media/contractfirsttypes.png "ContractFirstTypes")  
  
 Os tipos gerados pela ferramenta são criados no arquivo GeneratedXSDTypes.cs. O arquivo é criado na \<diretório do projeto > /obj/\<configuração de compilação > diretório /XSDGeneratedCode/ por padrão. O esquema de exemplo no início deste tópico é convertido da seguinte maneira:  
  
```csharp
//------------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by a tool.  
//     Runtime Version:4.0.30319.17330  
//  
//     Changes to this file may cause incorrect behavior and will be lost if  
//     the code is regenerated.  
// </auto-generated>  
//------------------------------------------------------------------------------  
  
namespace TestXSD3.ContractTypes  
{  
    using System.Xml.Serialization;  
  
    /// <remarks/>  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]  
    [System.SerializableAttribute()]  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.ComponentModel.DesignerCategoryAttribute("code")]  
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]  
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=true)]  
    public partial class SearchRequest  
    {  
  
        private string versionField;  
  
        private string marketField;  
  
        private string uILanguageField;  
  
        private string queryField;  
  
        private string appIdField;  
  
        private double latitudeField;  
  
        private bool latitudeFieldSpecified;  
  
        private double longitudeField;  
  
        private bool longitudeFieldSpecified;  
  
        private double radiusField;  
  
        private bool radiusFieldSpecified;  
  
        public SearchRequest()  
        {  
            this.versionField = "2.2";  
        }  
  
        /// <remarks/>  
        [System.ComponentModel.DefaultValueAttribute("2.2")]  
        public string Version  
        {  
            get  
            {  
                return this.versionField;  
            }  
            set  
            {  
                this.versionField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string Market  
        {  
            get  
            {  
                return this.marketField;  
            }  
            set  
            {  
                this.marketField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string UILanguage  
        {  
            get  
            {  
                return this.uILanguageField;  
            }  
            set  
            {  
                this.uILanguageField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string Query  
        {  
            get  
            {  
                return this.queryField;  
            }  
            set  
            {  
                this.queryField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string AppId  
        {  
            get  
            {  
                return this.appIdField;  
            }  
            set  
            {  
                this.appIdField = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Latitude  
        {  
            get  
            {  
                return this.latitudeField;  
            }  
            set  
            {  
                this.latitudeField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool LatitudeSpecified  
        {  
            get  
            {  
                return this.latitudeFieldSpecified;  
            }  
            set  
            {  
                this.latitudeFieldSpecified = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Longitude  
        {  
            get  
            {  
                return this.longitudeField;  
            }  
            set  
            {  
                this.longitudeField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool LongitudeSpecified  
        {  
            get  
            {  
                return this.longitudeFieldSpecified;  
            }  
            set  
            {  
                this.longitudeFieldSpecified = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Radius  
        {  
            get  
            {  
                return this.radiusField;  
            }  
            set  
            {  
                this.radiusField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool RadiusSpecified  
        {  
            get  
            {  
                return this.radiusFieldSpecified;  
            }  
            set  
            {  
                this.radiusFieldSpecified = value;  
            }  
        }  
    }  
  
    /// <remarks/>  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]  
    [System.SerializableAttribute()]  
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]  
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=false)]  
    public enum WebSearchOption  
    {  
  
        /// <remarks/>  
        DisableHostCollapsing,  
  
        /// <remarks/>  
        DisableQueryAlterations,  
    }  
}  
```  
  
## <a name="errors-and-warnings"></a>Erros e avisos  
 Erros e avisos encontrados ao analisar o esquema XSD aparecerão como erros e avisos de compilação.  
  
## <a name="interface-inheritance"></a>Herança de interface  
 Não é possível usar a herança de interface com o desenvolvimento de primeiro contrato; Isso é consistente com a maneira como as interfaces se comportam em outras operações. Para usar uma interface que herda de uma interface base, use dois pontos de extremidade separados. O primeiro ponto de extremidade usa o contrato herdado e o segundo ponto de extremidade implementa a interface base.
