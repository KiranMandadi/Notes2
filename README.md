Then it’s just this, from the project folder on the VM:

Stop the Console: Ctrl+C in its window, or end the Scheduled Task.
Pull and refresh:
   git pull origin main
   .venv\Scripts\Activate.ps1
   python -m pip install --no-deps -e .

The pip line takes a few seconds. It makes sure the new version number and any new files are picked up.
3. Start it again: crq ui, or run the Scheduled Task.
4. Check the version: turn on Technical details and look at the footer.

If the pull also changed requirements.lock, run python -m pip install -r requirements.lock as well. git pull lists the files it updated, so you’ll see whether it did.