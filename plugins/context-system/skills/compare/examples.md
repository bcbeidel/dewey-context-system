# Comparison Examples

Complete worked examples demonstrating both methods.

---

## Example 1: Cloud Provider Selection (Weighted Matrix)

**Scenario**: Choose cloud provider for new application

**Options**: AWS, Azure, GCP

**Criteria & Weights**:
- Cost (35%): Total 3-year TCO
- Performance (25%): Latency and throughput  
- Ecosystem (20%): Available services and integrations
- Familiarity (15%): Team experience
- Support (5%): Quality of documentation and support

**Scores**:
| Criterion | Weight | AWS | Azure | GCP |
|-----------|--------|-----|-------|-----|
| Cost | 35% | 7 (2.45) | 8 (2.80) | 9 (3.15) |
| Performance | 25% | 9 (2.25) | 8 (2.00) | 9 (2.25) |
| Ecosystem | 20% | 10 (2.00) | 8 (1.60) | 7 (1.40) |
| Familiarity | 15% | 9 (1.35) | 6 (0.90) | 5 (0.75) |
| Support | 5% | 8 (0.40) | 9 (0.45) | 7 (0.35) |
| **TOTAL** | **100%** | **8.45** | **7.75** | **7.90** |

**Recommendation**: AWS (8.45)
- Strongest ecosystem and team familiarity offset higher cost
- Performance tied with GCP
- Decision robust to ±10% weight changes

---

## Example 2: Product Strategy (Block Method)

**Scenario**: Choose between expanding existing product vs launching new product

**Dimensions**: Financial, Strategic, Operational, Risk

**Option 1: Expand Existing**
- Financial: $30M revenue potential (90% confidence), $5M investment
- Strategic: Deepens market position, defensive move
- Operational: Can execute with existing team, 12-month timeline
- Risk: Low (proven model), but limits long-term growth

**Option 2: Launch New**
- Financial: $50M revenue potential (60% confidence), $15M investment
- Strategic: Opens new market, offensive move
- Operational: Requires new capabilities, 18-24 month timeline
- Risk: High (unproven), but bigger upside

**Synthesis**: 
- Risk-adjusted: Option 1 = $27M expected value, Option 2 = $30M
- Strategic fit: Option 2 aligns better with 5-year vision
- Resource constraints: Option 1 executable now, Option 2 requires hiring

**Recommendation**: Option 2 (Launch New)
- Higher expected value despite higher risk
- Better strategic fit for growth ambitions
- Risk mitigatable through phased approach
- Accept 6-month delay to build capabilities
