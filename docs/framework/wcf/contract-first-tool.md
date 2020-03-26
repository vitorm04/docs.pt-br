---
title: Ferramenta Contract-First
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: 36e1a3e19f802ca5b74cf50f5bcd57c167e31e33
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291697"
---
# <a name="contract-first-tool"></a>Ferramenta Contract-First
Os contratos de serviço muitas vezes precisam ser criados a partir de serviços existentes. No .NET Framework 4.5 e posterior, as classes de contrato de dados podem ser criadas automaticamente a partir de serviços existentes usando a ferramenta contract-first. Para usar a ferramenta contract-first, o arquivo de definição de esquema XML (XSD) deve ser baixado localmente; a ferramenta não pode importar contratos de dados remotos via HTTP.

 A ferramenta de primeiro contrato é integrada ao Visual Studio 2012 como uma tarefa de construção. Os arquivos de código gerados pela tarefa de compilação são criados toda vez que o projeto é construído, para que o projeto possa facilmente adotar alterações no contrato de serviço subjacente.

 Os tipos de esquema que a ferramenta contract-first pode importar incluem os seguintes:

```xml
<xsd:complexType>
 <xsd:simpleType>
 </xsd:simpleType>
</xsd:complexType>
```

 Tipos simples não serão gerados se `Int16` forem primitivos como ou; `String` tipos complexos não serão gerados `Collection`se forem do tipo . Os tipos também não serão gerados `xsd:complexType`se fizerem parte de outro . Em todos esses casos, os tipos serão referenciados aos tipos existentes no projeto.

## <a name="adding-a-data-contract-to-a-project"></a>Adicionando um contrato de dados a um projeto
 Antes que a primeira ferramenta seja utilizada, o contrato de serviço (XSD) deve ser adicionado ao projeto. Para efeitos desta visão geral, o contrato a seguir será usado para ilustrar as funções de contrato-primeiro. Esta definição de serviço é um pequeno subconjunto do contrato de serviço usado pela API de pesquisa de Bing.

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

 Para adicionar o contrato de serviço acima ao projeto, clique com o botão direito do mouse no projeto e selecione **Adicionar novo...**. Selecione A definição de esquema no painel WCF da caixa de diálogo Modelos e nomeie o novo arquivo SampleContract.xsd. Copie e cole o código acima na exibição de código do novo arquivo.

## <a name="configuring-contract-first-options"></a>Configuração de opções de contrato-primeiro
 As opções de contrato-primeiro podem ser configuradas no menu Propriedades de um projeto WCF. Para habilitar o desenvolvimento do contrato primeiro, selecione a caixa de seleção **Ativar XSD como definição de tipo idioma** na página WCF da janela propriedades do projeto.

 ![Captura de tela das opções WCF com o desenvolvimento do primeiro contrato ativado.](./media/contract-first-tool/contract-first-options.png)

 Para configurar propriedades avançadas, clique no botão Avançado.

 ![Caixa de diálogo Configurações avançadas de geração de código de contrato.](./media/contract-first-tool/advanced-contract-settings.png)

 As seguintes configurações avançadas podem ser configuradas para geração de código a partir de contratos. As configurações só podem ser configuradas para todos os arquivos do projeto; as configurações não podem ser configuradas para arquivos individuais neste momento.

- **Modo serializador**: Esta configuração determina qual serializador é usado para ler arquivos de contrato de serviço. Quando **o XML Serializer** é selecionado, as opções **Tipos de coleta** e tipos de **reutilização** são desativadas. Essas opções só se aplicam ao **Serializador de Contratos de Dados**.

- **Tipos de reutilização**: Esta configuração especifica quais bibliotecas são usadas para reutilização do tipo. Esta configuração só se aplica se **o modo Serializer** estiver definido como **Serializador de contrato de dados**.

- **Tipo de coleta**: Esta configuração especifica o tipo totalmente qualificado ou qualificado para montagem a ser usado para o tipo de dados de coleta. Esta configuração só se aplica se **o modo Serializer** estiver definido como **Serializador de contrato de dados**.

- **Tipo de dicionário**: Esta configuração especifica o tipo totalmente qualificado ou qualificado para montagem a ser usado para o tipo de dados do dicionário.

- **EnableDataBinding**: Esta configuração especifica <xref:System.ComponentModel.INotifyPropertyChanged> se deve implementar a interface em todos os tipos de dados para implementar a vinculação de dados.

- **Excluídos :Esta**configuração especifica a lista de tipos totalmente qualificados ou qualificados para montagem a serem excluídos das assembléias referenciadas. Esta configuração só se aplica se **o modo Serializer** estiver definido como **Serializador de contrato de dados**.

- **GenerateInternalTypes**: Esta configuração especifica se deve gerar classes marcadas como internas. Esta configuração só se aplica se **o modo Serializer** estiver definido como **Serializador de contrato de dados**.

- **GenerateSerializableTypes**: Esta configuração especifica se <xref:System.SerializableAttribute> deve gerar classes com o atributo. Esta configuração só se aplica se **o modo Serializer** estiver definido como **Serializador de contrato de dados**.

- **ImportXMLTypes**: Esta configuração especifica se deve configurar o <xref:System.SerializableAttribute> serializador <xref:System.Runtime.Serialization.DataContractAttribute> de contrato de dados para aplicar o atributo às classes sem o atributo.  Esta configuração só se aplica se **o modo Serializer** estiver definido como **Serializador de contrato de dados**.

- **SuporteFx35TypedDataSets**: Esta configuração especifica se deve fornecer funcionalidade adicional para conjuntos de dados digitados criados para o .NET Framework 3.5. Quando **o modo Serializer** estiver definido <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> como **XML Serializer,** a extensão será adicionada ao importador de esquemas XML quando este valor for definido como True. Quando **o Modo Serializador** estiver definido <xref:System.DateTimeOffset> como **Serializador de Contrato de Dados,** o tipo <xref:System.DateTimeOffset> será excluído das Referências quando esse valor for definido como Falso, de modo que a seja sempre gerada para versões de framework mais antigas.

- **InputXsdFiles**: Esta configuração especifica a lista de arquivos de entrada. Cada arquivo deve conter um esquema XML válido.

- **Idioma**: Esta configuração especifica a linguagem do código do contrato gerado. A configuração deve <xref:System.CodeDom.Compiler.CodeDomProvider>ser reconhecível por .

- **NamespaceMapeamentos**: Esta configuração especifica os mapeamentos dos namespaces de destino XSD para os namespaces clr. Cada mapeamento deve usar o seguinte formato:

    ```xml
    "Schema Namespace, CLR Namespace"
    ```

     O Serializador XML só aceita um mapeamento no seguinte formato:

    ```xml
    "*, CLR Namespace"
    ```

- **Diretório de saída**: Esta configuração especifica o diretório onde os arquivos de código serão gerados.

 As configurações serão usadas para gerar tipos de contrato de serviço a partir dos arquivos do contrato de serviço quando o projeto for construído.

## <a name="using-contract-first-development"></a>Usando o desenvolvimento de contrato-primeiro
 Após adicionar o contrato de serviço ao projeto e confirmar as configurações de construção, construa o projeto pressionando **F6**. Os tipos definidos no contrato de serviço estarão então disponíveis para uso no projeto.

 Para usar os tipos definidos no contrato `ContractTypes` de serviço, adicione uma referência ao espaço de nome atual:

```csharp
using MyProjectNamespace.ContractTypes;
```

 Os tipos definidos no contrato de prestação de serviços serão então solucionáveis no projeto, conforme mostrado abaixo:

 ![PesquisaA classe SearchRequest exibida no IntelliSense depois de digitar as primeiras letras.](./media/contract-first-tool/service-contract-types.png)

 Os tipos gerados pela ferramenta são criados no arquivo GeneratedXSDTypes.cs. O arquivo é criado \<no diretório de projeto\<>/obj/ configuração de compilação>/XSDGeneratedCode/diretório por padrão. O esquema amostral no início deste artigo é convertido da seguinte forma:

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
 Erros e avisos encontrados na análise do esquema XSD aparecerão como erros de compilação e avisos.

## <a name="interface-inheritance"></a>Herança de interface
 Não é possível usar a herança de interface com o desenvolvimento do contrato-primeiro; isso é consistente com a forma como as interfaces se comportam em outras operações. Para usar uma interface que herda uma interface base, use dois pontos finais separados. O primeiro ponto final usa o contrato herdado, e o segundo ponto final implementa a interface base.
