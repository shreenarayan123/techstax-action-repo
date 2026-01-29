# Action Repo - GitHub Webhook Trigger Repository

This repository is used to trigger GitHub webhook events. Any **Push**, **Pull Request**, or **Merge** action in this repository will send webhook events to the configured endpoint.

## 🔗 Linked Webhook

This repository is configured to send webhooks to the **webhook-repo** Flask application.

## ⚙️ Webhook Configuration

To set up the webhook:

1. Go to **Settings** → **Webhooks** in this repository
2. Click **"Add webhook"**
3. Configure:
   - **Payload URL**: Your webhook-repo endpoint (e.g., `https://your-server.com/webhook/receiver`)
   - **Content type**: `application/json`
   - **Secret**: (optional) Your webhook secret
   - **Events**: Select:
     - ✅ Pushes
     - ✅ Pull requests

## 🧪 Testing

### Test Push Event
```bash
# Make a change and push
echo "test" >> test.txt
git add .
git commit -m "Test push event"
git push
```

### Test Pull Request Event
```bash
# Create a new branch
git checkout -b feature/test-pr

# Make changes
echo "feature" >> feature.txt
git add .
git commit -m "Add feature"
git push -u origin feature/test-pr

# Create PR via GitHub UI
```

### Test Merge Event
1. Create a Pull Request
2. Merge it via GitHub UI
3. The webhook will detect it as a MERGE action

## 📊 Supported Events

| Event | Webhook Action |
|-------|----------------|
| Push to any branch | `PUSH` |
| Open Pull Request | `PULL_REQUEST` |
| Close PR (merged) | `MERGE` |

## 📝 Sample Files

- `sample.txt` - A sample file for testing push events
