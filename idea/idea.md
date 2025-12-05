# Batch Optical Archivist - Project Idea

## Summary

A batch M-Disc archiving tool for burning family photos/videos (particularly of Ezra's first months) to 25GB M-Discs.

## Core Requirements

1. **Input**: Point GUI to a directory (on mounted NAS) containing files to archive
2. **Batching**: Automatically group files into ~24GB batches (leaving headroom on the 25GB disc)
3. **Workflow**: Sequential burning - "first disc ready" → burn → "next disc ready" → repeat
4. **Backend**: Can wrap K3B if it has CLI access (Pioneer burner works well with K3B)

## Key Feature

**Copy multiplier**: Option to burn each batch 1-5 times (for offsite copies to send to in-laws)

## Problem It Solves

Eliminates manual folder creation/sizing - currently requires manually creating subfolders, filling them to 24GB in K3B, burning, and repeating. This tool automates that batching logic.

## Implementation Notes

- Python/Qt GUI
- Scans the source directory
- Calculates optimal file batching to ~24GB chunks
- Shows batch queue with disc numbers
- Interfaces with K3B CLI (`k3b --datacd`) or `growisofs`/`wodim` directly
- Supports 1-5x copy per batch
