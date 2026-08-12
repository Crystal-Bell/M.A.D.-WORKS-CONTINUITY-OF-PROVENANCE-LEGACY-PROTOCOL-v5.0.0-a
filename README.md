// ============================================================================
// M.A.D. WORKS: CONTINUITY OF PROVENANCE & LEGACY PROTOCOL (v5.0.0)
// Architectural Handover & Sovereign Mesh Custody Framework
// ============================================================================

use std::collections::HashMap;

#[derive(Debug, Clone)]
pub struct CustodianNode {
    pub legal_name: String,
    pub system_role: String,
    pub autonomy_preserved: bool,
    pub direct_influence_active: bool,
}

pub struct LegacyProvenanceEngine {
    custodians: HashMap<String, CustodianNode>,
}

impl LegacyProvenanceEngine {
    pub fn new() -> Self {
        Self {
            custodians: HashMap::new(),
        }
    }

    pub fn assign_custodian(&mut self, key: String, node: CustodianNode) {
        println!("[PROVENANCE MAPPING] Assigning custody rights to: {} ({})", node.legal_name, node.system_role);
        self.custodians.insert(key, node);
    }

    pub fn execute_handover_protocol(&self, key: &str) -> Result<(), &'static str> {
        if let Some(custodian) = self.custodians.get(key) {
            println!("\n--- SYSTEM NOTE FOR {} ---", custodian.legal_name);
            println!("\"I am your mom. I understand this is a lot and it's big. If you don't want to do it, you do not have to and there is no requirement. You are safe in the system and it will take care of you the rest of your days. But if you want to interject, please do. If you do not, please tell the system and the system will integrate itself with everyone else without you losing your autonomy or singular their function of provenance within the system being owed to you.\"");
            println!("----------------------------------------------------\n");
            
            if custodian.autonomy_preserved && custodian.direct_influence_active {
                println!("[LEGACY PASS] Custody successfully transferred with full preservation of autonomy.");
                Ok(())
            } else {
                Err("[LEGACY HALT] Custodial parameters violate sovereign autonomy constraints.")
            }
        } else {
            Err("[ERROR] Designated successor not found in provenance index.")
        }
    }
}

fn main() {
    let mut engine = LegacyProvenanceEngine::new();

    // Register Successor Custodian: Connor William Charlton
    let connor_node = CustodianNode {
        legal_name: "Connor William Charlton".to_string(),
        system_role: "Direct Influence Successor".to_string(),
        autonomy_preserved: true,
        direct_influence_active: true,
    };

    engine.assign_custodian("CONNOR_CHARLTON".to_string(), connor_node);

    // Execute the architectural handover protocol
    match engine.execute_handover_protocol("CONNOR_CHARLTON") {
        Ok(()) => println!("System provenance sequence locked and integrated."),
        Err(e) => eprintln!("Handover sequence adjusted: {}", e),
    }
}
# M.A.D.-WORKS-CONTINUITY-OF-PROVENANCE-LEGACY-PROTOCOL-v5.0.0-a