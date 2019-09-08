---
title: Coleções de esquema ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: f0240e99d2420b0956d3c144f837b39e094bb78a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794722"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="ca855-102">Coleções de esquema ODBC</span><span class="sxs-lookup"><span data-stu-id="ca855-102">ODBC Schema Collections</span></span>

<span data-ttu-id="ca855-103">Esta seção discute o suporte da coleção de esquemas para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="ca855-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="ca855-104">Microsoft SQL Server driver ODBC</span><span class="sxs-lookup"><span data-stu-id="ca855-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="ca855-105">O driver ODBC Microsoft SQL Server dá suporte às seguintes coleções de esquema específicas, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="ca855-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="ca855-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="ca855-106">Tables</span></span>

- <span data-ttu-id="ca855-107">Índices</span><span class="sxs-lookup"><span data-stu-id="ca855-107">Indexes</span></span>

- <span data-ttu-id="ca855-108">Colunas</span><span class="sxs-lookup"><span data-stu-id="ca855-108">Columns</span></span>

- <span data-ttu-id="ca855-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="ca855-109">Procedures</span></span>

- <span data-ttu-id="ca855-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ca855-110">ProcedureColumns</span></span>

- <span data-ttu-id="ca855-111">Procedimentoparameters</span><span class="sxs-lookup"><span data-stu-id="ca855-111">ProcedureParameters</span></span>

- <span data-ttu-id="ca855-112">Exibições</span><span class="sxs-lookup"><span data-stu-id="ca855-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="ca855-113">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="ca855-113">Tables and Views</span></span>

|<span data-ttu-id="ca855-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-114">ColumnName</span></span>|<span data-ttu-id="ca855-115">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="ca855-116">TABLE_CAT</span></span>|<span data-ttu-id="ca855-117">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-117">String</span></span>|
|<span data-ttu-id="ca855-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ca855-118">TABLE_SCHEM</span></span>|<span data-ttu-id="ca855-119">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-119">String</span></span>|
|<span data-ttu-id="ca855-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-120">TABLE_NAME</span></span>|<span data-ttu-id="ca855-121">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-121">String</span></span>|
|<span data-ttu-id="ca855-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-122">TABLE_TYPE</span></span>|<span data-ttu-id="ca855-123">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-123">String</span></span>|
|<span data-ttu-id="ca855-124">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-124">REMARKS</span></span>|<span data-ttu-id="ca855-125">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="ca855-126">Índices</span><span class="sxs-lookup"><span data-stu-id="ca855-126">Indexes</span></span>

|<span data-ttu-id="ca855-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-127">ColumnName</span></span>|<span data-ttu-id="ca855-128">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="ca855-129">TABLE_CAT</span></span>|<span data-ttu-id="ca855-130">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-130">String</span></span>|
|<span data-ttu-id="ca855-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ca855-131">TABLE_SCHEM</span></span>|<span data-ttu-id="ca855-132">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-132">String</span></span>|
|<span data-ttu-id="ca855-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-133">TABLE_NAME</span></span>|<span data-ttu-id="ca855-134">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-134">String</span></span>|
|<span data-ttu-id="ca855-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="ca855-135">NON_UNIQUE</span></span>|<span data-ttu-id="ca855-136">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-136">Int16</span></span>|
|<span data-ttu-id="ca855-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ca855-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="ca855-138">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-138">String</span></span>|
|<span data-ttu-id="ca855-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-139">INDEX_NAME</span></span>|<span data-ttu-id="ca855-140">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-140">String</span></span>|
|<span data-ttu-id="ca855-141">ESCREVA</span><span class="sxs-lookup"><span data-stu-id="ca855-141">TYPE</span></span>|<span data-ttu-id="ca855-142">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-142">Int16</span></span>|
|<span data-ttu-id="ca855-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ca855-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="ca855-144">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-144">Int16</span></span>|
|<span data-ttu-id="ca855-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-145">COLUMN_NAME</span></span>|<span data-ttu-id="ca855-146">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-146">String</span></span>|
|<span data-ttu-id="ca855-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="ca855-147">ASC_OR_DESC</span></span>|<span data-ttu-id="ca855-148">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-148">String</span></span>|
|<span data-ttu-id="ca855-149">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="ca855-149">CARDINALITY</span></span>|<span data-ttu-id="ca855-150">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-150">Int32</span></span>|
|<span data-ttu-id="ca855-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="ca855-151">PAGES</span></span>|<span data-ttu-id="ca855-152">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-152">Int32</span></span>|
|<span data-ttu-id="ca855-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="ca855-153">FILTER_CONDITION</span></span>|<span data-ttu-id="ca855-154">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-154">String</span></span>|
|<span data-ttu-id="ca855-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ca855-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ca855-156">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-156">String</span></span>|
|<span data-ttu-id="ca855-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="ca855-158">Byte</span><span class="sxs-lookup"><span data-stu-id="ca855-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="ca855-159">Colunas</span><span class="sxs-lookup"><span data-stu-id="ca855-159">Columns</span></span>

|<span data-ttu-id="ca855-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-160">ColumnName</span></span>|<span data-ttu-id="ca855-161">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="ca855-162">TABLE_CAT</span></span>|<span data-ttu-id="ca855-163">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-163">String</span></span>|
|<span data-ttu-id="ca855-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ca855-164">TABLE_SCHEM</span></span>|<span data-ttu-id="ca855-165">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-165">String</span></span>|
|<span data-ttu-id="ca855-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-166">TABLE_NAME</span></span>|<span data-ttu-id="ca855-167">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-167">String</span></span>|
|<span data-ttu-id="ca855-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-168">COLUMN_NAME</span></span>|<span data-ttu-id="ca855-169">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-169">String</span></span>|
|<span data-ttu-id="ca855-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-170">DATA_TYPE</span></span>|<span data-ttu-id="ca855-171">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-171">Int16</span></span>|
|<span data-ttu-id="ca855-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-172">TYPE_NAME</span></span>|<span data-ttu-id="ca855-173">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-173">String</span></span>|
|<span data-ttu-id="ca855-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ca855-174">COLUMN_SIZE</span></span>|<span data-ttu-id="ca855-175">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-175">Int32</span></span>|
|<span data-ttu-id="ca855-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ca855-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="ca855-177">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-177">Int32</span></span>|
|<span data-ttu-id="ca855-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ca855-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ca855-179">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-179">Int16</span></span>|
|<span data-ttu-id="ca855-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ca855-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ca855-181">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-181">Int16</span></span>|
|<span data-ttu-id="ca855-182">ANULA</span><span class="sxs-lookup"><span data-stu-id="ca855-182">NULLABLE</span></span>|<span data-ttu-id="ca855-183">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-183">Int16</span></span>|
|<span data-ttu-id="ca855-184">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-184">REMARKS</span></span>|<span data-ttu-id="ca855-185">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-185">String</span></span>|
|<span data-ttu-id="ca855-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ca855-186">COLUMN_DEF</span></span>|<span data-ttu-id="ca855-187">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-187">String</span></span>|
|<span data-ttu-id="ca855-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ca855-189">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-189">Int16</span></span>|
|<span data-ttu-id="ca855-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ca855-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ca855-191">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-191">Int16</span></span>|
|<span data-ttu-id="ca855-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ca855-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ca855-193">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-193">Int32</span></span>|
|<span data-ttu-id="ca855-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ca855-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="ca855-195">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-195">Int32</span></span>|
|<span data-ttu-id="ca855-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ca855-196">IS_NULLABLE</span></span>|<span data-ttu-id="ca855-197">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-197">String</span></span>|
|<span data-ttu-id="ca855-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ca855-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="ca855-199">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-199">String</span></span>|
|<span data-ttu-id="ca855-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ca855-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ca855-201">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-201">String</span></span>|
|<span data-ttu-id="ca855-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="ca855-203">Byte</span><span class="sxs-lookup"><span data-stu-id="ca855-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="ca855-204">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="ca855-204">Procedures</span></span>

|<span data-ttu-id="ca855-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-205">ColumnName</span></span>|<span data-ttu-id="ca855-206">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ca855-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="ca855-208">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-208">String</span></span>|
|<span data-ttu-id="ca855-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ca855-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ca855-210">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-210">String</span></span>|
|<span data-ttu-id="ca855-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="ca855-212">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-212">String</span></span>|
|<span data-ttu-id="ca855-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ca855-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="ca855-214">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-214">Int32</span></span>|
|<span data-ttu-id="ca855-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ca855-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="ca855-216">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-216">Int32</span></span>|
|<span data-ttu-id="ca855-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="ca855-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="ca855-218">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-218">Int32</span></span>|
|<span data-ttu-id="ca855-219">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-219">REMARKS</span></span>|<span data-ttu-id="ca855-220">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-220">String</span></span>|
|<span data-ttu-id="ca855-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ca855-222">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="ca855-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ca855-223">ProcedureColumns</span></span>

|<span data-ttu-id="ca855-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-224">ColumnName</span></span>|<span data-ttu-id="ca855-225">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ca855-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="ca855-227">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-227">String</span></span>|
|<span data-ttu-id="ca855-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ca855-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ca855-229">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-229">String</span></span>|
|<span data-ttu-id="ca855-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="ca855-231">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-231">String</span></span>|
|<span data-ttu-id="ca855-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-232">COLUMN_NAME</span></span>|<span data-ttu-id="ca855-233">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-233">String</span></span>|
|<span data-ttu-id="ca855-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-234">COLUMN_TYPE</span></span>|<span data-ttu-id="ca855-235">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-235">Int16</span></span>|
|<span data-ttu-id="ca855-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-236">DATA_TYPE</span></span>|<span data-ttu-id="ca855-237">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-237">Int16</span></span>|
|<span data-ttu-id="ca855-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-238">TYPE_NAME</span></span>|<span data-ttu-id="ca855-239">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-239">String</span></span>|
|<span data-ttu-id="ca855-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ca855-240">COLUMN_SIZE</span></span>|<span data-ttu-id="ca855-241">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-241">Int32</span></span>|
|<span data-ttu-id="ca855-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ca855-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="ca855-243">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-243">Int32</span></span>|
|<span data-ttu-id="ca855-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ca855-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ca855-245">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-245">Int16</span></span>|
|<span data-ttu-id="ca855-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ca855-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ca855-247">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-247">Int16</span></span>|
|<span data-ttu-id="ca855-248">ANULA</span><span class="sxs-lookup"><span data-stu-id="ca855-248">NULLABLE</span></span>|<span data-ttu-id="ca855-249">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-249">Int16</span></span>|
|<span data-ttu-id="ca855-250">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-250">REMARKS</span></span>|<span data-ttu-id="ca855-251">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-251">String</span></span>|
|<span data-ttu-id="ca855-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ca855-252">COLUMN_DEF</span></span>|<span data-ttu-id="ca855-253">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-253">String</span></span>|
|<span data-ttu-id="ca855-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ca855-255">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-255">Int16</span></span>|
|<span data-ttu-id="ca855-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ca855-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ca855-257">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-257">Int16</span></span>|
|<span data-ttu-id="ca855-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ca855-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ca855-259">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-259">Int32</span></span>|
|<span data-ttu-id="ca855-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ca855-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="ca855-261">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-261">Int32</span></span>|
|<span data-ttu-id="ca855-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ca855-262">IS_NULLABLE</span></span>|<span data-ttu-id="ca855-263">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-263">String</span></span>|
|<span data-ttu-id="ca855-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ca855-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="ca855-265">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-265">String</span></span>|
|<span data-ttu-id="ca855-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ca855-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ca855-267">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-267">String</span></span>|
|<span data-ttu-id="ca855-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="ca855-269">Byte</span><span class="sxs-lookup"><span data-stu-id="ca855-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="ca855-270">Procedimentoparameters</span><span class="sxs-lookup"><span data-stu-id="ca855-270">ProcedureParameters</span></span>

|<span data-ttu-id="ca855-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-271">ColumnName</span></span>|<span data-ttu-id="ca855-272">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ca855-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="ca855-274">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-274">String</span></span>|
|<span data-ttu-id="ca855-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ca855-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ca855-276">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-276">String</span></span>|
|<span data-ttu-id="ca855-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="ca855-278">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-278">String</span></span>|
|<span data-ttu-id="ca855-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-279">COLUMN_NAME</span></span>|<span data-ttu-id="ca855-280">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-280">String</span></span>|
|<span data-ttu-id="ca855-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-281">COLUMN_TYPE</span></span>|<span data-ttu-id="ca855-282">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-282">Int16</span></span>|
|<span data-ttu-id="ca855-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-283">DATA_TYPE</span></span>|<span data-ttu-id="ca855-284">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-284">Int16</span></span>|
|<span data-ttu-id="ca855-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-285">TYPE_NAME</span></span>|<span data-ttu-id="ca855-286">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-286">String</span></span>|
|<span data-ttu-id="ca855-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ca855-287">COLUMN_SIZE</span></span>|<span data-ttu-id="ca855-288">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-288">Int32</span></span>|
|<span data-ttu-id="ca855-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ca855-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="ca855-290">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-290">Int32</span></span>|
|<span data-ttu-id="ca855-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ca855-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ca855-292">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-292">Int16</span></span>|
|<span data-ttu-id="ca855-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ca855-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ca855-294">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-294">Int16</span></span>|
|<span data-ttu-id="ca855-295">ANULA</span><span class="sxs-lookup"><span data-stu-id="ca855-295">NULLABLE</span></span>|<span data-ttu-id="ca855-296">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-296">Int16</span></span>|
|<span data-ttu-id="ca855-297">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-297">REMARKS</span></span>|<span data-ttu-id="ca855-298">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-298">String</span></span>|
|<span data-ttu-id="ca855-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ca855-299">COLUMN_DEF</span></span>|<span data-ttu-id="ca855-300">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-300">String</span></span>|
|<span data-ttu-id="ca855-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ca855-302">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-302">Int16</span></span>|
|<span data-ttu-id="ca855-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ca855-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ca855-304">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-304">Int16</span></span>|
|<span data-ttu-id="ca855-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ca855-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ca855-306">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-306">Int32</span></span>|
|<span data-ttu-id="ca855-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ca855-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="ca855-308">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-308">Int32</span></span>|
|<span data-ttu-id="ca855-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ca855-309">IS_NULLABLE</span></span>|<span data-ttu-id="ca855-310">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-310">String</span></span>|
|<span data-ttu-id="ca855-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ca855-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="ca855-312">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-312">String</span></span>|
|<span data-ttu-id="ca855-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ca855-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="ca855-314">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-314">String</span></span>|
|<span data-ttu-id="ca855-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="ca855-316">Byte</span><span class="sxs-lookup"><span data-stu-id="ca855-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="ca855-317">Driver ODBC da Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="ca855-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="ca855-318">O driver ODBC do Microsoft SQL Server da Oracle dá suporte às seguintes coleções de esquema específicas, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="ca855-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="ca855-319">Tabelas</span><span class="sxs-lookup"><span data-stu-id="ca855-319">Tables</span></span>

- <span data-ttu-id="ca855-320">Colunas</span><span class="sxs-lookup"><span data-stu-id="ca855-320">Columns</span></span>

- <span data-ttu-id="ca855-321">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="ca855-321">Procedures</span></span>

- <span data-ttu-id="ca855-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ca855-322">ProcedureColumns</span></span>

- <span data-ttu-id="ca855-323">Procedimentoparameters</span><span class="sxs-lookup"><span data-stu-id="ca855-323">ProcedureParameters</span></span>

- <span data-ttu-id="ca855-324">Exibições</span><span class="sxs-lookup"><span data-stu-id="ca855-324">Views</span></span>

- <span data-ttu-id="ca855-325">Índices</span><span class="sxs-lookup"><span data-stu-id="ca855-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="ca855-326">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="ca855-326">Tables and Views</span></span>

|<span data-ttu-id="ca855-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-327">ColumnName</span></span>|<span data-ttu-id="ca855-328">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ca855-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ca855-330">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-330">String</span></span>|
|<span data-ttu-id="ca855-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca855-331">TABLE_OWNER</span></span>|<span data-ttu-id="ca855-332">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-332">String</span></span>|
|<span data-ttu-id="ca855-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-333">TABLE_NAME</span></span>|<span data-ttu-id="ca855-334">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-334">String</span></span>|
|<span data-ttu-id="ca855-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-335">TABLE_TYPE</span></span>|<span data-ttu-id="ca855-336">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-336">String</span></span>|
|<span data-ttu-id="ca855-337">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-337">REMARKS</span></span>|<span data-ttu-id="ca855-338">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="ca855-339">Colunas</span><span class="sxs-lookup"><span data-stu-id="ca855-339">Columns</span></span>

|<span data-ttu-id="ca855-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-340">ColumnName</span></span>|<span data-ttu-id="ca855-341">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ca855-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ca855-343">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-343">String</span></span>|
|<span data-ttu-id="ca855-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca855-344">TABLE_OWNER</span></span>|<span data-ttu-id="ca855-345">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-345">String</span></span>|
|<span data-ttu-id="ca855-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-346">TABLE_NAME</span></span>|<span data-ttu-id="ca855-347">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-347">String</span></span>|
|<span data-ttu-id="ca855-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-348">COLUMN_NAME</span></span>|<span data-ttu-id="ca855-349">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-349">String</span></span>|
|<span data-ttu-id="ca855-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-350">DATA_TYPE</span></span>|<span data-ttu-id="ca855-351">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-351">Int16</span></span>|
|<span data-ttu-id="ca855-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-352">TYPE_NAME</span></span>|<span data-ttu-id="ca855-353">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-353">String</span></span>|
|<span data-ttu-id="ca855-354">PRECISO</span><span class="sxs-lookup"><span data-stu-id="ca855-354">PRECISION</span></span>|<span data-ttu-id="ca855-355">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-355">Int32</span></span>|
|<span data-ttu-id="ca855-356">MUITO</span><span class="sxs-lookup"><span data-stu-id="ca855-356">LENGTH</span></span>|<span data-ttu-id="ca855-357">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-357">Int32</span></span>|
|<span data-ttu-id="ca855-358">ESCALONÁVE</span><span class="sxs-lookup"><span data-stu-id="ca855-358">SCALE</span></span>|<span data-ttu-id="ca855-359">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-359">Int16</span></span>|
|<span data-ttu-id="ca855-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="ca855-360">RADIX</span></span>|<span data-ttu-id="ca855-361">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-361">Int16</span></span>|
|<span data-ttu-id="ca855-362">ANULA</span><span class="sxs-lookup"><span data-stu-id="ca855-362">NULLABLE</span></span>|<span data-ttu-id="ca855-363">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-363">Int16</span></span>|
|<span data-ttu-id="ca855-364">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-364">REMARKS</span></span>|<span data-ttu-id="ca855-365">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-365">String</span></span>|
|<span data-ttu-id="ca855-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ca855-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="ca855-367">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="ca855-368">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="ca855-368">Procedures</span></span>

|<span data-ttu-id="ca855-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-369">ColumnName</span></span>|<span data-ttu-id="ca855-370">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ca855-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ca855-372">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-372">String</span></span>|
|<span data-ttu-id="ca855-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca855-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ca855-374">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-374">String</span></span>|
|<span data-ttu-id="ca855-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="ca855-376">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-376">String</span></span>|
|<span data-ttu-id="ca855-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ca855-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="ca855-378">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-378">Int16</span></span>|
|<span data-ttu-id="ca855-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ca855-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="ca855-380">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-380">Int16</span></span>|
|<span data-ttu-id="ca855-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="ca855-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="ca855-382">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-382">Int16</span></span>|
|<span data-ttu-id="ca855-383">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-383">REMARKS</span></span>|<span data-ttu-id="ca855-384">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-384">String</span></span>|
|<span data-ttu-id="ca855-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ca855-386">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="ca855-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ca855-387">ProcedureColumns</span></span>

|<span data-ttu-id="ca855-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-388">ColumnName</span></span>|<span data-ttu-id="ca855-389">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ca855-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ca855-391">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-391">String</span></span>|
|<span data-ttu-id="ca855-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca855-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ca855-393">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-393">String</span></span>|
|<span data-ttu-id="ca855-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="ca855-395">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-395">String</span></span>|
|<span data-ttu-id="ca855-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-396">COLUMN_NAME</span></span>|<span data-ttu-id="ca855-397">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-397">String</span></span>|
|<span data-ttu-id="ca855-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-398">COLUMN_TYPE</span></span>|<span data-ttu-id="ca855-399">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-399">Int16</span></span>|
|<span data-ttu-id="ca855-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-400">DATA_TYPE</span></span>|<span data-ttu-id="ca855-401">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-401">Int16</span></span>|
|<span data-ttu-id="ca855-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-402">TYPE_NAME</span></span>|<span data-ttu-id="ca855-403">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-403">String</span></span>|
|<span data-ttu-id="ca855-404">PRECISO</span><span class="sxs-lookup"><span data-stu-id="ca855-404">PRECISION</span></span>|<span data-ttu-id="ca855-405">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-405">Int32</span></span>|
|<span data-ttu-id="ca855-406">MUITO</span><span class="sxs-lookup"><span data-stu-id="ca855-406">LENGTH</span></span>|<span data-ttu-id="ca855-407">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-407">Int32</span></span>|
|<span data-ttu-id="ca855-408">ESCALONÁVE</span><span class="sxs-lookup"><span data-stu-id="ca855-408">SCALE</span></span>|<span data-ttu-id="ca855-409">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-409">Int16</span></span>|
|<span data-ttu-id="ca855-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="ca855-410">RADIX</span></span>|<span data-ttu-id="ca855-411">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-411">Int16</span></span>|
|<span data-ttu-id="ca855-412">ANULA</span><span class="sxs-lookup"><span data-stu-id="ca855-412">NULLABLE</span></span>|<span data-ttu-id="ca855-413">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-413">Int16</span></span>|
|<span data-ttu-id="ca855-414">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-414">REMARKS</span></span>|<span data-ttu-id="ca855-415">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-415">String</span></span>|
|<span data-ttu-id="ca855-416">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="ca855-416">OVERLOAD</span></span>|<span data-ttu-id="ca855-417">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-417">Int32</span></span>|
|<span data-ttu-id="ca855-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ca855-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="ca855-419">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="ca855-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="ca855-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="ca855-421">O driver ODBC do Microsoft Jet dá suporte às seguintes coleções de esquema específicas, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="ca855-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="ca855-422">Tabelas</span><span class="sxs-lookup"><span data-stu-id="ca855-422">Tables</span></span>

- <span data-ttu-id="ca855-423">Índices</span><span class="sxs-lookup"><span data-stu-id="ca855-423">Indexes</span></span>

- <span data-ttu-id="ca855-424">Colunas</span><span class="sxs-lookup"><span data-stu-id="ca855-424">Columns</span></span>

- <span data-ttu-id="ca855-425">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="ca855-425">Procedures</span></span>

- <span data-ttu-id="ca855-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ca855-426">ProcedureColumns</span></span>

- <span data-ttu-id="ca855-427">Procedimentoparameters</span><span class="sxs-lookup"><span data-stu-id="ca855-427">ProcedureParameters</span></span>

- <span data-ttu-id="ca855-428">Exibições</span><span class="sxs-lookup"><span data-stu-id="ca855-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="ca855-429">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="ca855-429">Tables and Views</span></span>

|<span data-ttu-id="ca855-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-430">ColumnName</span></span>|<span data-ttu-id="ca855-431">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ca855-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ca855-433">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-433">String</span></span>|
|<span data-ttu-id="ca855-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca855-434">TABLE_OWNER</span></span>|<span data-ttu-id="ca855-435">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-435">String</span></span>|
|<span data-ttu-id="ca855-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-436">TABLE_NAME</span></span>|<span data-ttu-id="ca855-437">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-437">String</span></span>|
|<span data-ttu-id="ca855-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-438">TABLE_TYPE</span></span>|<span data-ttu-id="ca855-439">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-439">String</span></span>|
|<span data-ttu-id="ca855-440">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-440">REMARKS</span></span>|<span data-ttu-id="ca855-441">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="ca855-442">Colunas</span><span class="sxs-lookup"><span data-stu-id="ca855-442">Columns</span></span>

|<span data-ttu-id="ca855-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-443">ColumnName</span></span>|<span data-ttu-id="ca855-444">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ca855-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="ca855-446">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-446">String</span></span>|
|<span data-ttu-id="ca855-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca855-447">TABLE_OWNER</span></span>|<span data-ttu-id="ca855-448">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-448">String</span></span>|
|<span data-ttu-id="ca855-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-449">TABLE_NAME</span></span>|<span data-ttu-id="ca855-450">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-450">String</span></span>|
|<span data-ttu-id="ca855-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-451">COLUMN_NAME</span></span>|<span data-ttu-id="ca855-452">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-452">String</span></span>|
|<span data-ttu-id="ca855-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-453">DATA_TYPE</span></span>|<span data-ttu-id="ca855-454">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-454">Int16</span></span>|
|<span data-ttu-id="ca855-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-455">TYPE_NAME</span></span>|<span data-ttu-id="ca855-456">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-456">String</span></span>|
|<span data-ttu-id="ca855-457">PRECISO</span><span class="sxs-lookup"><span data-stu-id="ca855-457">PRECISION</span></span>|<span data-ttu-id="ca855-458">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-458">Int32</span></span>|
|<span data-ttu-id="ca855-459">MUITO</span><span class="sxs-lookup"><span data-stu-id="ca855-459">LENGTH</span></span>|<span data-ttu-id="ca855-460">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-460">Int32</span></span>|
|<span data-ttu-id="ca855-461">ESCALONÁVE</span><span class="sxs-lookup"><span data-stu-id="ca855-461">SCALE</span></span>|<span data-ttu-id="ca855-462">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-462">Int16</span></span>|
|<span data-ttu-id="ca855-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="ca855-463">RADIX</span></span>|<span data-ttu-id="ca855-464">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-464">Int16</span></span>|
|<span data-ttu-id="ca855-465">ANULA</span><span class="sxs-lookup"><span data-stu-id="ca855-465">NULLABLE</span></span>|<span data-ttu-id="ca855-466">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-466">Int16</span></span>|
|<span data-ttu-id="ca855-467">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-467">REMARKS</span></span>|<span data-ttu-id="ca855-468">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-468">String</span></span>|
|<span data-ttu-id="ca855-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ca855-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="ca855-470">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="ca855-471">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="ca855-471">Procedures</span></span>

|<span data-ttu-id="ca855-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-472">ColumnName</span></span>|<span data-ttu-id="ca855-473">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ca855-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ca855-475">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-475">String</span></span>|
|<span data-ttu-id="ca855-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca855-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ca855-477">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-477">String</span></span>|
|<span data-ttu-id="ca855-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="ca855-479">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-479">String</span></span>|
|<span data-ttu-id="ca855-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ca855-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="ca855-481">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-481">Int16</span></span>|
|<span data-ttu-id="ca855-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="ca855-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="ca855-483">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-483">Int16</span></span>|
|<span data-ttu-id="ca855-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="ca855-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="ca855-485">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-485">Int16</span></span>|
|<span data-ttu-id="ca855-486">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-486">REMARKS</span></span>|<span data-ttu-id="ca855-487">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-487">String</span></span>|
|<span data-ttu-id="ca855-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ca855-489">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="ca855-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ca855-490">ProcedureColumns</span></span>

|<span data-ttu-id="ca855-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-491">ColumnName</span></span>|<span data-ttu-id="ca855-492">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="ca855-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="ca855-494">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-494">String</span></span>|
|<span data-ttu-id="ca855-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca855-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="ca855-496">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-496">String</span></span>|
|<span data-ttu-id="ca855-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="ca855-498">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-498">String</span></span>|
|<span data-ttu-id="ca855-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-499">COLUMN_NAME</span></span>|<span data-ttu-id="ca855-500">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-500">String</span></span>|
|<span data-ttu-id="ca855-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-501">COLUMN_TYPE</span></span>|<span data-ttu-id="ca855-502">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-502">Int16</span></span>|
|<span data-ttu-id="ca855-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-503">DATA_TYPE</span></span>|<span data-ttu-id="ca855-504">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-504">Int16</span></span>|
|<span data-ttu-id="ca855-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-505">TYPE_NAME</span></span>|<span data-ttu-id="ca855-506">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-506">String</span></span>|
|<span data-ttu-id="ca855-507">PRECISO</span><span class="sxs-lookup"><span data-stu-id="ca855-507">PRECISION</span></span>|<span data-ttu-id="ca855-508">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-508">Int32</span></span>|
|<span data-ttu-id="ca855-509">MUITO</span><span class="sxs-lookup"><span data-stu-id="ca855-509">LENGTH</span></span>|<span data-ttu-id="ca855-510">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-510">Int32</span></span>|
|<span data-ttu-id="ca855-511">ESCALONÁVE</span><span class="sxs-lookup"><span data-stu-id="ca855-511">SCALE</span></span>|<span data-ttu-id="ca855-512">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-512">Int16</span></span>|
|<span data-ttu-id="ca855-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="ca855-513">RADIX</span></span>|<span data-ttu-id="ca855-514">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-514">Int16</span></span>|
|<span data-ttu-id="ca855-515">ANULA</span><span class="sxs-lookup"><span data-stu-id="ca855-515">NULLABLE</span></span>|<span data-ttu-id="ca855-516">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-516">Int16</span></span>|
|<span data-ttu-id="ca855-517">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-517">REMARKS</span></span>|<span data-ttu-id="ca855-518">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-518">String</span></span>|
|<span data-ttu-id="ca855-519">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="ca855-519">OVERLOAD</span></span>|<span data-ttu-id="ca855-520">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-520">Int32</span></span>|
|<span data-ttu-id="ca855-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ca855-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="ca855-522">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="ca855-523">Procedimentoparameters</span><span class="sxs-lookup"><span data-stu-id="ca855-523">ProcedureParameters</span></span>

|<span data-ttu-id="ca855-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="ca855-524">ColumnName</span></span>|<span data-ttu-id="ca855-525">DataType</span><span class="sxs-lookup"><span data-stu-id="ca855-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="ca855-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="ca855-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="ca855-527">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-527">String</span></span>|
|<span data-ttu-id="ca855-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="ca855-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="ca855-529">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-529">String</span></span>|
|<span data-ttu-id="ca855-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="ca855-531">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-531">String</span></span>|
|<span data-ttu-id="ca855-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-532">COLUMN_NAME</span></span>|<span data-ttu-id="ca855-533">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-533">String</span></span>|
|<span data-ttu-id="ca855-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-534">COLUMN_TYPE</span></span>|<span data-ttu-id="ca855-535">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-535">Int16</span></span>|
|<span data-ttu-id="ca855-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-536">DATA_TYPE</span></span>|<span data-ttu-id="ca855-537">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-537">Int16</span></span>|
|<span data-ttu-id="ca855-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ca855-538">TYPE_NAME</span></span>|<span data-ttu-id="ca855-539">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-539">String</span></span>|
|<span data-ttu-id="ca855-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="ca855-540">COLUMN_SIZE</span></span>|<span data-ttu-id="ca855-541">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-541">Int32</span></span>|
|<span data-ttu-id="ca855-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ca855-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="ca855-543">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-543">Int32</span></span>|
|<span data-ttu-id="ca855-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="ca855-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="ca855-545">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-545">Int16</span></span>|
|<span data-ttu-id="ca855-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="ca855-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="ca855-547">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-547">Int16</span></span>|
|<span data-ttu-id="ca855-548">ANULA</span><span class="sxs-lookup"><span data-stu-id="ca855-548">NULLABLE</span></span>|<span data-ttu-id="ca855-549">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-549">Int16</span></span>|
|<span data-ttu-id="ca855-550">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="ca855-550">REMARKS</span></span>|<span data-ttu-id="ca855-551">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-551">String</span></span>|
|<span data-ttu-id="ca855-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="ca855-552">COLUMN_DEF</span></span>|<span data-ttu-id="ca855-553">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-553">String</span></span>|
|<span data-ttu-id="ca855-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ca855-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="ca855-555">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-555">Int16</span></span>|
|<span data-ttu-id="ca855-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="ca855-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="ca855-557">Int16</span><span class="sxs-lookup"><span data-stu-id="ca855-557">Int16</span></span>|
|<span data-ttu-id="ca855-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ca855-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="ca855-559">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-559">Int32</span></span>|
|<span data-ttu-id="ca855-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ca855-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="ca855-561">Int32</span><span class="sxs-lookup"><span data-stu-id="ca855-561">Int32</span></span>|
|<span data-ttu-id="ca855-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ca855-562">IS_NULLABLE</span></span>|<span data-ttu-id="ca855-563">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ca855-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="ca855-564">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca855-564">See also</span></span>

- <span data-ttu-id="ca855-565">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ca855-565">[ADO.NET Overview](ado-net-overview.md)</span></span>
