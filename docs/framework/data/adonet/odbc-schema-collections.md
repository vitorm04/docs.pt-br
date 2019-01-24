---
title: Coleções de esquema ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: 072a9cd365031cd5660d1824bc229d459abc5af8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525827"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="75f57-102">Coleções de esquema ODBC</span><span class="sxs-lookup"><span data-stu-id="75f57-102">ODBC Schema Collections</span></span>
<span data-ttu-id="75f57-103">Esta seção discute o suporte de coleção de esquema para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="75f57-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="75f57-104">Driver ODBC do Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="75f57-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="75f57-105">O Driver ODBC do Microsoft SQL Server suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="75f57-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="75f57-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="75f57-106">Tables</span></span>  
  
-   <span data-ttu-id="75f57-107">Índices</span><span class="sxs-lookup"><span data-stu-id="75f57-107">Indexes</span></span>  
  
-   <span data-ttu-id="75f57-108">Colunas</span><span class="sxs-lookup"><span data-stu-id="75f57-108">Columns</span></span>  
  
-   <span data-ttu-id="75f57-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="75f57-109">Procedures</span></span>  
  
-   <span data-ttu-id="75f57-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="75f57-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="75f57-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="75f57-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="75f57-112">Exibições</span><span class="sxs-lookup"><span data-stu-id="75f57-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="75f57-113">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="75f57-113">Tables and Views</span></span>  
  
|<span data-ttu-id="75f57-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-114">ColumnName</span></span>|<span data-ttu-id="75f57-115">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="75f57-116">TABLE_CAT</span></span>|<span data-ttu-id="75f57-117">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-117">String</span></span>|  
|<span data-ttu-id="75f57-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="75f57-118">TABLE_SCHEM</span></span>|<span data-ttu-id="75f57-119">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-119">String</span></span>|  
|<span data-ttu-id="75f57-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-120">TABLE_NAME</span></span>|<span data-ttu-id="75f57-121">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-121">String</span></span>|  
|<span data-ttu-id="75f57-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-122">TABLE_TYPE</span></span>|<span data-ttu-id="75f57-123">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-123">String</span></span>|  
|<span data-ttu-id="75f57-124">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-124">REMARKS</span></span>|<span data-ttu-id="75f57-125">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="75f57-126">Índices</span><span class="sxs-lookup"><span data-stu-id="75f57-126">Indexes</span></span>  
  
|<span data-ttu-id="75f57-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-127">ColumnName</span></span>|<span data-ttu-id="75f57-128">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="75f57-129">TABLE_CAT</span></span>|<span data-ttu-id="75f57-130">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-130">String</span></span>|  
|<span data-ttu-id="75f57-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="75f57-131">TABLE_SCHEM</span></span>|<span data-ttu-id="75f57-132">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-132">String</span></span>|  
|<span data-ttu-id="75f57-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-133">TABLE_NAME</span></span>|<span data-ttu-id="75f57-134">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-134">String</span></span>|  
|<span data-ttu-id="75f57-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="75f57-135">NON_UNIQUE</span></span>|<span data-ttu-id="75f57-136">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-136">Int16</span></span>|  
|<span data-ttu-id="75f57-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="75f57-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="75f57-138">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-138">String</span></span>|  
|<span data-ttu-id="75f57-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-139">INDEX_NAME</span></span>|<span data-ttu-id="75f57-140">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-140">String</span></span>|  
|<span data-ttu-id="75f57-141">TIPO</span><span class="sxs-lookup"><span data-stu-id="75f57-141">TYPE</span></span>|<span data-ttu-id="75f57-142">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-142">Int16</span></span>|  
|<span data-ttu-id="75f57-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="75f57-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="75f57-144">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-144">Int16</span></span>|  
|<span data-ttu-id="75f57-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-145">COLUMN_NAME</span></span>|<span data-ttu-id="75f57-146">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-146">String</span></span>|  
|<span data-ttu-id="75f57-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="75f57-147">ASC_OR_DESC</span></span>|<span data-ttu-id="75f57-148">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-148">String</span></span>|  
|<span data-ttu-id="75f57-149">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="75f57-149">CARDINATLITY</span></span>|<span data-ttu-id="75f57-150">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-150">Int32</span></span>|  
|<span data-ttu-id="75f57-151">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="75f57-151">PAGES</span></span>|<span data-ttu-id="75f57-152">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-152">Int32</span></span>|  
|<span data-ttu-id="75f57-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="75f57-153">FILTER_CONDITION</span></span>|<span data-ttu-id="75f57-154">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-154">String</span></span>|  
|<span data-ttu-id="75f57-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="75f57-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="75f57-156">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-156">String</span></span>|  
|<span data-ttu-id="75f57-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="75f57-158">Byte</span><span class="sxs-lookup"><span data-stu-id="75f57-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="75f57-159">Colunas</span><span class="sxs-lookup"><span data-stu-id="75f57-159">Columns</span></span>  
  
|<span data-ttu-id="75f57-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-160">ColumnName</span></span>|<span data-ttu-id="75f57-161">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="75f57-162">TABLE_CAT</span></span>|<span data-ttu-id="75f57-163">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-163">String</span></span>|  
|<span data-ttu-id="75f57-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="75f57-164">TABLE_SCHEM</span></span>|<span data-ttu-id="75f57-165">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-165">String</span></span>|  
|<span data-ttu-id="75f57-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-166">TABLE_NAME</span></span>|<span data-ttu-id="75f57-167">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-167">String</span></span>|  
|<span data-ttu-id="75f57-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-168">COLUMN_NAME</span></span>|<span data-ttu-id="75f57-169">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-169">String</span></span>|  
|<span data-ttu-id="75f57-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-170">DATA_TYPE</span></span>|<span data-ttu-id="75f57-171">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-171">Int16</span></span>|  
|<span data-ttu-id="75f57-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-172">TYPE_NAME</span></span>|<span data-ttu-id="75f57-173">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-173">String</span></span>|  
|<span data-ttu-id="75f57-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="75f57-174">COLUMN_SIZE</span></span>|<span data-ttu-id="75f57-175">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-175">Int32</span></span>|  
|<span data-ttu-id="75f57-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="75f57-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="75f57-177">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-177">Int32</span></span>|  
|<span data-ttu-id="75f57-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="75f57-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="75f57-179">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-179">Int16</span></span>|  
|<span data-ttu-id="75f57-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="75f57-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="75f57-181">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-181">Int16</span></span>|  
|<span data-ttu-id="75f57-182">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="75f57-182">NULLABLE</span></span>|<span data-ttu-id="75f57-183">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-183">Int16</span></span>|  
|<span data-ttu-id="75f57-184">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-184">REMARKS</span></span>|<span data-ttu-id="75f57-185">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-185">String</span></span>|  
|<span data-ttu-id="75f57-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="75f57-186">COLUMN_DEF</span></span>|<span data-ttu-id="75f57-187">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-187">String</span></span>|  
|<span data-ttu-id="75f57-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="75f57-189">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-189">Int16</span></span>|  
|<span data-ttu-id="75f57-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="75f57-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="75f57-191">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-191">Int16</span></span>|  
|<span data-ttu-id="75f57-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="75f57-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="75f57-193">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-193">Int32</span></span>|  
|<span data-ttu-id="75f57-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="75f57-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="75f57-195">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-195">Int32</span></span>|  
|<span data-ttu-id="75f57-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="75f57-196">IS_NULLABLE</span></span>|<span data-ttu-id="75f57-197">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-197">String</span></span>|  
|<span data-ttu-id="75f57-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="75f57-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="75f57-199">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-199">String</span></span>|  
|<span data-ttu-id="75f57-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="75f57-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="75f57-201">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-201">String</span></span>|  
|<span data-ttu-id="75f57-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="75f57-203">Byte</span><span class="sxs-lookup"><span data-stu-id="75f57-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="75f57-204">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="75f57-204">Procedures</span></span>  
  
|<span data-ttu-id="75f57-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-205">ColumnName</span></span>|<span data-ttu-id="75f57-206">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="75f57-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="75f57-208">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-208">String</span></span>|  
|<span data-ttu-id="75f57-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="75f57-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="75f57-210">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-210">String</span></span>|  
|<span data-ttu-id="75f57-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="75f57-212">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-212">String</span></span>|  
|<span data-ttu-id="75f57-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="75f57-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="75f57-214">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-214">Int32</span></span>|  
|<span data-ttu-id="75f57-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="75f57-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="75f57-216">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-216">Int32</span></span>|  
|<span data-ttu-id="75f57-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="75f57-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="75f57-218">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-218">Int32</span></span>|  
|<span data-ttu-id="75f57-219">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-219">REMARKS</span></span>|<span data-ttu-id="75f57-220">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-220">String</span></span>|  
|<span data-ttu-id="75f57-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="75f57-222">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="75f57-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="75f57-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="75f57-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-224">ColumnName</span></span>|<span data-ttu-id="75f57-225">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="75f57-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="75f57-227">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-227">String</span></span>|  
|<span data-ttu-id="75f57-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="75f57-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="75f57-229">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-229">String</span></span>|  
|<span data-ttu-id="75f57-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="75f57-231">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-231">String</span></span>|  
|<span data-ttu-id="75f57-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-232">COLUMN_NAME</span></span>|<span data-ttu-id="75f57-233">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-233">String</span></span>|  
|<span data-ttu-id="75f57-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-234">COLUMN_TYPE</span></span>|<span data-ttu-id="75f57-235">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-235">Int16</span></span>|  
|<span data-ttu-id="75f57-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-236">DATA_TYPE</span></span>|<span data-ttu-id="75f57-237">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-237">Int16</span></span>|  
|<span data-ttu-id="75f57-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-238">TYPE_NAME</span></span>|<span data-ttu-id="75f57-239">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-239">String</span></span>|  
|<span data-ttu-id="75f57-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="75f57-240">COLUMN_SIZE</span></span>|<span data-ttu-id="75f57-241">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-241">Int32</span></span>|  
|<span data-ttu-id="75f57-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="75f57-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="75f57-243">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-243">Int32</span></span>|  
|<span data-ttu-id="75f57-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="75f57-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="75f57-245">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-245">Int16</span></span>|  
|<span data-ttu-id="75f57-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="75f57-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="75f57-247">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-247">Int16</span></span>|  
|<span data-ttu-id="75f57-248">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="75f57-248">NULLABLE</span></span>|<span data-ttu-id="75f57-249">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-249">Int16</span></span>|  
|<span data-ttu-id="75f57-250">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-250">REMARKS</span></span>|<span data-ttu-id="75f57-251">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-251">String</span></span>|  
|<span data-ttu-id="75f57-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="75f57-252">COLUMN_DEF</span></span>|<span data-ttu-id="75f57-253">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-253">String</span></span>|  
|<span data-ttu-id="75f57-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="75f57-255">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-255">Int16</span></span>|  
|<span data-ttu-id="75f57-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="75f57-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="75f57-257">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-257">Int16</span></span>|  
|<span data-ttu-id="75f57-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="75f57-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="75f57-259">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-259">Int32</span></span>|  
|<span data-ttu-id="75f57-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="75f57-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="75f57-261">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-261">Int32</span></span>|  
|<span data-ttu-id="75f57-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="75f57-262">IS_NULLABLE</span></span>|<span data-ttu-id="75f57-263">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-263">String</span></span>|  
|<span data-ttu-id="75f57-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="75f57-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="75f57-265">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-265">String</span></span>|  
|<span data-ttu-id="75f57-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="75f57-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="75f57-267">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-267">String</span></span>|  
|<span data-ttu-id="75f57-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="75f57-269">Byte</span><span class="sxs-lookup"><span data-stu-id="75f57-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="75f57-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="75f57-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="75f57-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-271">ColumnName</span></span>|<span data-ttu-id="75f57-272">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="75f57-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="75f57-274">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-274">String</span></span>|  
|<span data-ttu-id="75f57-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="75f57-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="75f57-276">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-276">String</span></span>|  
|<span data-ttu-id="75f57-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="75f57-278">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-278">String</span></span>|  
|<span data-ttu-id="75f57-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-279">COLUMN_NAME</span></span>|<span data-ttu-id="75f57-280">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-280">String</span></span>|  
|<span data-ttu-id="75f57-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-281">COLUMN_TYPE</span></span>|<span data-ttu-id="75f57-282">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-282">Int16</span></span>|  
|<span data-ttu-id="75f57-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-283">DATA_TYPE</span></span>|<span data-ttu-id="75f57-284">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-284">Int16</span></span>|  
|<span data-ttu-id="75f57-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-285">TYPE_NAME</span></span>|<span data-ttu-id="75f57-286">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-286">String</span></span>|  
|<span data-ttu-id="75f57-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="75f57-287">COLUMN_SIZE</span></span>|<span data-ttu-id="75f57-288">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-288">Int32</span></span>|  
|<span data-ttu-id="75f57-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="75f57-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="75f57-290">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-290">Int32</span></span>|  
|<span data-ttu-id="75f57-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="75f57-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="75f57-292">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-292">Int16</span></span>|  
|<span data-ttu-id="75f57-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="75f57-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="75f57-294">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-294">Int16</span></span>|  
|<span data-ttu-id="75f57-295">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="75f57-295">NULLABLE</span></span>|<span data-ttu-id="75f57-296">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-296">Int16</span></span>|  
|<span data-ttu-id="75f57-297">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-297">REMARKS</span></span>|<span data-ttu-id="75f57-298">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-298">String</span></span>|  
|<span data-ttu-id="75f57-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="75f57-299">COLUMN_DEF</span></span>|<span data-ttu-id="75f57-300">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-300">String</span></span>|  
|<span data-ttu-id="75f57-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="75f57-302">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-302">Int16</span></span>|  
|<span data-ttu-id="75f57-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="75f57-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="75f57-304">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-304">Int16</span></span>|  
|<span data-ttu-id="75f57-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="75f57-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="75f57-306">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-306">Int32</span></span>|  
|<span data-ttu-id="75f57-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="75f57-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="75f57-308">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-308">Int32</span></span>|  
|<span data-ttu-id="75f57-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="75f57-309">IS_NULLABLE</span></span>|<span data-ttu-id="75f57-310">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-310">String</span></span>|  
|<span data-ttu-id="75f57-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="75f57-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="75f57-312">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-312">String</span></span>|  
|<span data-ttu-id="75f57-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="75f57-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="75f57-314">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-314">String</span></span>|  
|<span data-ttu-id="75f57-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="75f57-316">Byte</span><span class="sxs-lookup"><span data-stu-id="75f57-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="75f57-317">Driver ODBC do Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="75f57-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="75f57-318">O Driver ODBC do Microsoft SQL Server Oracle suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="75f57-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="75f57-319">Tabelas</span><span class="sxs-lookup"><span data-stu-id="75f57-319">Tables</span></span>  
  
-   <span data-ttu-id="75f57-320">Colunas</span><span class="sxs-lookup"><span data-stu-id="75f57-320">Columns</span></span>  
  
-   <span data-ttu-id="75f57-321">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="75f57-321">Procedures</span></span>  
  
-   <span data-ttu-id="75f57-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="75f57-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="75f57-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="75f57-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="75f57-324">Exibições</span><span class="sxs-lookup"><span data-stu-id="75f57-324">Views</span></span>  
  
-   <span data-ttu-id="75f57-325">Índices</span><span class="sxs-lookup"><span data-stu-id="75f57-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="75f57-326">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="75f57-326">Tables and Views</span></span>  
  
|<span data-ttu-id="75f57-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-327">ColumnName</span></span>|<span data-ttu-id="75f57-328">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="75f57-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="75f57-330">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-330">String</span></span>|  
|<span data-ttu-id="75f57-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="75f57-331">TABLE_OWNER</span></span>|<span data-ttu-id="75f57-332">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-332">String</span></span>|  
|<span data-ttu-id="75f57-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-333">TABLE_NAME</span></span>|<span data-ttu-id="75f57-334">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-334">String</span></span>|  
|<span data-ttu-id="75f57-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-335">TABLE_TYPE</span></span>|<span data-ttu-id="75f57-336">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-336">String</span></span>|  
|<span data-ttu-id="75f57-337">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-337">REMARKS</span></span>|<span data-ttu-id="75f57-338">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="75f57-339">Colunas</span><span class="sxs-lookup"><span data-stu-id="75f57-339">Columns</span></span>  
  
|<span data-ttu-id="75f57-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-340">ColumnName</span></span>|<span data-ttu-id="75f57-341">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="75f57-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="75f57-343">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-343">String</span></span>|  
|<span data-ttu-id="75f57-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="75f57-344">TABLE_OWNER</span></span>|<span data-ttu-id="75f57-345">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-345">String</span></span>|  
|<span data-ttu-id="75f57-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-346">TABLE_NAME</span></span>|<span data-ttu-id="75f57-347">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-347">String</span></span>|  
|<span data-ttu-id="75f57-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-348">COLUMN_NAME</span></span>|<span data-ttu-id="75f57-349">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-349">String</span></span>|  
|<span data-ttu-id="75f57-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-350">DATA_TYPE</span></span>|<span data-ttu-id="75f57-351">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-351">Int16</span></span>|  
|<span data-ttu-id="75f57-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-352">TYPE_NAME</span></span>|<span data-ttu-id="75f57-353">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-353">String</span></span>|  
|<span data-ttu-id="75f57-354">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="75f57-354">PRECISION</span></span>|<span data-ttu-id="75f57-355">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-355">Int32</span></span>|  
|<span data-ttu-id="75f57-356">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="75f57-356">LENGTH</span></span>|<span data-ttu-id="75f57-357">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-357">Int32</span></span>|  
|<span data-ttu-id="75f57-358">ESCALA</span><span class="sxs-lookup"><span data-stu-id="75f57-358">SCALE</span></span>|<span data-ttu-id="75f57-359">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-359">Int16</span></span>|  
|<span data-ttu-id="75f57-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="75f57-360">RADIX</span></span>|<span data-ttu-id="75f57-361">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-361">Int16</span></span>|  
|<span data-ttu-id="75f57-362">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="75f57-362">NULLABLE</span></span>|<span data-ttu-id="75f57-363">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-363">Int16</span></span>|  
|<span data-ttu-id="75f57-364">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-364">REMARKS</span></span>|<span data-ttu-id="75f57-365">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-365">String</span></span>|  
|<span data-ttu-id="75f57-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="75f57-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="75f57-367">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="75f57-368">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="75f57-368">Procedures</span></span>  
  
|<span data-ttu-id="75f57-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-369">ColumnName</span></span>|<span data-ttu-id="75f57-370">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="75f57-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="75f57-372">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-372">String</span></span>|  
|<span data-ttu-id="75f57-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="75f57-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="75f57-374">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-374">String</span></span>|  
|<span data-ttu-id="75f57-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="75f57-376">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-376">String</span></span>|  
|<span data-ttu-id="75f57-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="75f57-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="75f57-378">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-378">Int16</span></span>|  
|<span data-ttu-id="75f57-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="75f57-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="75f57-380">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-380">Int16</span></span>|  
|<span data-ttu-id="75f57-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="75f57-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="75f57-382">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-382">Int16</span></span>|  
|<span data-ttu-id="75f57-383">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-383">REMARKS</span></span>|<span data-ttu-id="75f57-384">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-384">String</span></span>|  
|<span data-ttu-id="75f57-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="75f57-386">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="75f57-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="75f57-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="75f57-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-388">ColumnName</span></span>|<span data-ttu-id="75f57-389">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="75f57-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="75f57-391">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-391">String</span></span>|  
|<span data-ttu-id="75f57-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="75f57-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="75f57-393">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-393">String</span></span>|  
|<span data-ttu-id="75f57-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="75f57-395">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-395">String</span></span>|  
|<span data-ttu-id="75f57-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-396">COLUMN_NAME</span></span>|<span data-ttu-id="75f57-397">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-397">String</span></span>|  
|<span data-ttu-id="75f57-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-398">COLUMN_TYPE</span></span>|<span data-ttu-id="75f57-399">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-399">Int16</span></span>|  
|<span data-ttu-id="75f57-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-400">DATA_TYPE</span></span>|<span data-ttu-id="75f57-401">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-401">Int16</span></span>|  
|<span data-ttu-id="75f57-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-402">TYPE_NAME</span></span>|<span data-ttu-id="75f57-403">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-403">String</span></span>|  
|<span data-ttu-id="75f57-404">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="75f57-404">PRECISION</span></span>|<span data-ttu-id="75f57-405">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-405">Int32</span></span>|  
|<span data-ttu-id="75f57-406">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="75f57-406">LENGTH</span></span>|<span data-ttu-id="75f57-407">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-407">Int32</span></span>|  
|<span data-ttu-id="75f57-408">ESCALA</span><span class="sxs-lookup"><span data-stu-id="75f57-408">SCALE</span></span>|<span data-ttu-id="75f57-409">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-409">Int16</span></span>|  
|<span data-ttu-id="75f57-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="75f57-410">RADIX</span></span>|<span data-ttu-id="75f57-411">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-411">Int16</span></span>|  
|<span data-ttu-id="75f57-412">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="75f57-412">NULLABLE</span></span>|<span data-ttu-id="75f57-413">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-413">Int16</span></span>|  
|<span data-ttu-id="75f57-414">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-414">REMARKS</span></span>|<span data-ttu-id="75f57-415">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-415">String</span></span>|  
|<span data-ttu-id="75f57-416">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="75f57-416">OVERLOAD</span></span>|<span data-ttu-id="75f57-417">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-417">Int32</span></span>|  
|<span data-ttu-id="75f57-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="75f57-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="75f57-419">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="75f57-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="75f57-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="75f57-421">O Driver ODBC do Microsoft Jet suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="75f57-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="75f57-422">Tabelas</span><span class="sxs-lookup"><span data-stu-id="75f57-422">Tables</span></span>  
  
-   <span data-ttu-id="75f57-423">Índices</span><span class="sxs-lookup"><span data-stu-id="75f57-423">Indexes</span></span>  
  
-   <span data-ttu-id="75f57-424">Colunas</span><span class="sxs-lookup"><span data-stu-id="75f57-424">Columns</span></span>  
  
-   <span data-ttu-id="75f57-425">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="75f57-425">Procedures</span></span>  
  
-   <span data-ttu-id="75f57-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="75f57-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="75f57-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="75f57-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="75f57-428">Exibições</span><span class="sxs-lookup"><span data-stu-id="75f57-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="75f57-429">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="75f57-429">Tables and Views</span></span>  
  
|<span data-ttu-id="75f57-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-430">ColumnName</span></span>|<span data-ttu-id="75f57-431">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="75f57-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="75f57-433">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-433">String</span></span>|  
|<span data-ttu-id="75f57-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="75f57-434">TABLE_OWNER</span></span>|<span data-ttu-id="75f57-435">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-435">String</span></span>|  
|<span data-ttu-id="75f57-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-436">TABLE_NAME</span></span>|<span data-ttu-id="75f57-437">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-437">String</span></span>|  
|<span data-ttu-id="75f57-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-438">TABLE_TYPE</span></span>|<span data-ttu-id="75f57-439">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-439">String</span></span>|  
|<span data-ttu-id="75f57-440">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-440">REMARKS</span></span>|<span data-ttu-id="75f57-441">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="75f57-442">Colunas</span><span class="sxs-lookup"><span data-stu-id="75f57-442">Columns</span></span>  
  
|<span data-ttu-id="75f57-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-443">ColumnName</span></span>|<span data-ttu-id="75f57-444">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="75f57-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="75f57-446">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-446">String</span></span>|  
|<span data-ttu-id="75f57-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="75f57-447">TABLE_OWNER</span></span>|<span data-ttu-id="75f57-448">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-448">String</span></span>|  
|<span data-ttu-id="75f57-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-449">TABLE_NAME</span></span>|<span data-ttu-id="75f57-450">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-450">String</span></span>|  
|<span data-ttu-id="75f57-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-451">COLUMN_NAME</span></span>|<span data-ttu-id="75f57-452">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-452">String</span></span>|  
|<span data-ttu-id="75f57-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-453">DATA_TYPE</span></span>|<span data-ttu-id="75f57-454">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-454">Int16</span></span>|  
|<span data-ttu-id="75f57-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-455">TYPE_NAME</span></span>|<span data-ttu-id="75f57-456">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-456">String</span></span>|  
|<span data-ttu-id="75f57-457">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="75f57-457">PRECISION</span></span>|<span data-ttu-id="75f57-458">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-458">Int32</span></span>|  
|<span data-ttu-id="75f57-459">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="75f57-459">LENGTH</span></span>|<span data-ttu-id="75f57-460">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-460">Int32</span></span>|  
|<span data-ttu-id="75f57-461">ESCALA</span><span class="sxs-lookup"><span data-stu-id="75f57-461">SCALE</span></span>|<span data-ttu-id="75f57-462">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-462">Int16</span></span>|  
|<span data-ttu-id="75f57-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="75f57-463">RADIX</span></span>|<span data-ttu-id="75f57-464">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-464">Int16</span></span>|  
|<span data-ttu-id="75f57-465">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="75f57-465">NULLABLE</span></span>|<span data-ttu-id="75f57-466">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-466">Int16</span></span>|  
|<span data-ttu-id="75f57-467">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-467">REMARKS</span></span>|<span data-ttu-id="75f57-468">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-468">String</span></span>|  
|<span data-ttu-id="75f57-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="75f57-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="75f57-470">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="75f57-471">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="75f57-471">Procedures</span></span>  
  
|<span data-ttu-id="75f57-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-472">ColumnName</span></span>|<span data-ttu-id="75f57-473">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="75f57-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="75f57-475">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-475">String</span></span>|  
|<span data-ttu-id="75f57-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="75f57-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="75f57-477">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-477">String</span></span>|  
|<span data-ttu-id="75f57-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="75f57-479">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-479">String</span></span>|  
|<span data-ttu-id="75f57-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="75f57-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="75f57-481">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-481">Int16</span></span>|  
|<span data-ttu-id="75f57-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="75f57-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="75f57-483">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-483">Int16</span></span>|  
|<span data-ttu-id="75f57-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="75f57-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="75f57-485">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-485">Int16</span></span>|  
|<span data-ttu-id="75f57-486">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-486">REMARKS</span></span>|<span data-ttu-id="75f57-487">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-487">String</span></span>|  
|<span data-ttu-id="75f57-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="75f57-489">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="75f57-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="75f57-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="75f57-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-491">ColumnName</span></span>|<span data-ttu-id="75f57-492">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="75f57-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="75f57-494">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-494">String</span></span>|  
|<span data-ttu-id="75f57-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="75f57-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="75f57-496">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-496">String</span></span>|  
|<span data-ttu-id="75f57-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="75f57-498">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-498">String</span></span>|  
|<span data-ttu-id="75f57-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-499">COLUMN_NAME</span></span>|<span data-ttu-id="75f57-500">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-500">String</span></span>|  
|<span data-ttu-id="75f57-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-501">COLUMN_TYPE</span></span>|<span data-ttu-id="75f57-502">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-502">Int16</span></span>|  
|<span data-ttu-id="75f57-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-503">DATA_TYPE</span></span>|<span data-ttu-id="75f57-504">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-504">Int16</span></span>|  
|<span data-ttu-id="75f57-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-505">TYPE_NAME</span></span>|<span data-ttu-id="75f57-506">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-506">String</span></span>|  
|<span data-ttu-id="75f57-507">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="75f57-507">PRECISION</span></span>|<span data-ttu-id="75f57-508">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-508">Int32</span></span>|  
|<span data-ttu-id="75f57-509">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="75f57-509">LENGTH</span></span>|<span data-ttu-id="75f57-510">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-510">Int32</span></span>|  
|<span data-ttu-id="75f57-511">ESCALA</span><span class="sxs-lookup"><span data-stu-id="75f57-511">SCALE</span></span>|<span data-ttu-id="75f57-512">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-512">Int16</span></span>|  
|<span data-ttu-id="75f57-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="75f57-513">RADIX</span></span>|<span data-ttu-id="75f57-514">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-514">Int16</span></span>|  
|<span data-ttu-id="75f57-515">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="75f57-515">NULLABLE</span></span>|<span data-ttu-id="75f57-516">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-516">Int16</span></span>|  
|<span data-ttu-id="75f57-517">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-517">REMARKS</span></span>|<span data-ttu-id="75f57-518">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-518">String</span></span>|  
|<span data-ttu-id="75f57-519">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="75f57-519">OVERLOAD</span></span>|<span data-ttu-id="75f57-520">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-520">Int32</span></span>|  
|<span data-ttu-id="75f57-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="75f57-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="75f57-522">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="75f57-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="75f57-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="75f57-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="75f57-524">ColumnName</span></span>|<span data-ttu-id="75f57-525">DataType</span><span class="sxs-lookup"><span data-stu-id="75f57-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="75f57-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="75f57-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="75f57-527">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-527">String</span></span>|  
|<span data-ttu-id="75f57-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="75f57-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="75f57-529">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-529">String</span></span>|  
|<span data-ttu-id="75f57-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="75f57-531">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-531">String</span></span>|  
|<span data-ttu-id="75f57-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-532">COLUMN_NAME</span></span>|<span data-ttu-id="75f57-533">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-533">String</span></span>|  
|<span data-ttu-id="75f57-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-534">COLUMN_TYPE</span></span>|<span data-ttu-id="75f57-535">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-535">Int16</span></span>|  
|<span data-ttu-id="75f57-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-536">DATA_TYPE</span></span>|<span data-ttu-id="75f57-537">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-537">Int16</span></span>|  
|<span data-ttu-id="75f57-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="75f57-538">TYPE_NAME</span></span>|<span data-ttu-id="75f57-539">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-539">String</span></span>|  
|<span data-ttu-id="75f57-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="75f57-540">COLUMN_SIZE</span></span>|<span data-ttu-id="75f57-541">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-541">Int32</span></span>|  
|<span data-ttu-id="75f57-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="75f57-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="75f57-543">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-543">Int32</span></span>|  
|<span data-ttu-id="75f57-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="75f57-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="75f57-545">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-545">Int16</span></span>|  
|<span data-ttu-id="75f57-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="75f57-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="75f57-547">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-547">Int16</span></span>|  
|<span data-ttu-id="75f57-548">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="75f57-548">NULLABLE</span></span>|<span data-ttu-id="75f57-549">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-549">Int16</span></span>|  
|<span data-ttu-id="75f57-550">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="75f57-550">REMARKS</span></span>|<span data-ttu-id="75f57-551">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-551">String</span></span>|  
|<span data-ttu-id="75f57-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="75f57-552">COLUMN_DEF</span></span>|<span data-ttu-id="75f57-553">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-553">String</span></span>|  
|<span data-ttu-id="75f57-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="75f57-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="75f57-555">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-555">Int16</span></span>|  
|<span data-ttu-id="75f57-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="75f57-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="75f57-557">Int16</span><span class="sxs-lookup"><span data-stu-id="75f57-557">Int16</span></span>|  
|<span data-ttu-id="75f57-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="75f57-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="75f57-559">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-559">Int32</span></span>|  
|<span data-ttu-id="75f57-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="75f57-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="75f57-561">Int32</span><span class="sxs-lookup"><span data-stu-id="75f57-561">Int32</span></span>|  
|<span data-ttu-id="75f57-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="75f57-562">IS_NULLABLE</span></span>|<span data-ttu-id="75f57-563">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="75f57-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75f57-564">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75f57-564">See also</span></span>
- <span data-ttu-id="75f57-565">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="75f57-565">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
