# ==========================================
# Project: AmbitionHub
# Description:
# A central hub for ambitious coding projects, designed
# to support scalable systems and powerful ideas.
# ==========================================


# ---------- main.py ----------
"""
Main entry point for AmbitionHub.
"""

from core.scaling import ScalabilityEngine
from core.projects import ProjectHub


def run():
    print("🏗 AmbitionHub Initialized")
    print("🚀  Projects | 📈 Scalable Systems | 💡 Powerful Ideas\n")

    engine = ScalabilityEngine()
    hub = ProjectHub()

    data = [10, 20, 30, 40]

    # Run a scalable process
    print("⚙️ Processed Data:", engine.process_batch(lambda x: x * 3, data))

    # Evaluate system scalability
    print("📈 Scalability Score:", engine.scalability_score(data))

    # Register and list projects
    hub.register_project("AI Analyzer")
    hub.register_project("Distributed API")

    print("📂 Active Projects:", hub.list_projects())


if __name__ == "__main__":
    run()


# ---------- core/scaling.py ----------
"""
Scalability utilities for handling large workloads.
"""

import statistics

class ScalabilityEngine:
    """Engine designed for scalable processing."""

    def process_batch(self, func, items):
        """Apply a function efficiently across a dataset."""
        return [func(i) for i in items]

    def scalability_score(self, values):
        """
        Estimate scalability potential based on variance
        and dataset characteristics.
        """
        if not values:
            return 0

        variance = statistics.pvariance(values)
        base = sum(values) / len(values)

        return round(base / (1 + variance), 3)


# ---------- core/projects.py ----------
"""
Project hub management module.
"""

class ProjectHub:
    """Central registry for ambitious coding projects."""

    def __init__(self):
        self._projects = []

    def register_project(self, name: str):
        """Register a new project."""
        self._projects.append(name)

    def list_projects(self):
        """Return list of registered projects."""
        return self._projects


# ---------- tests/test_scaling.py ----------
"""
Tests for ScalabilityEngine.
"""

from core.scaling import ScalabilityEngine

def test_process_batch():
    engine = ScalabilityEngine()
    result = engine.process_batch(lambda x: x + 1, [1, 2, 3])
    assert result == [2, 3, 4]

def test_scalability_score():
    engine = ScalabilityEngine()
    score = engine.scalability_score([10, 20, 30])
    assert score > 0


# ---------- tests/test_projects.py ----------
"""
Tests for ProjectHub.
"""

from core.projects import ProjectHub

def test_project_registration():
    hub = ProjectHub()
    hub.register_project("Test Project")
    assert "Test Project" in hub.list_projects()
